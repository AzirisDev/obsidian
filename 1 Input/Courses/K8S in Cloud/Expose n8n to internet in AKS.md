To expose any application that we deployed to [[AKS - Azure Kubernetes Service]], we should simply created Kubernetes service with `LoadBalancer` type and deploy it. AKS creates Azure-side infrastructure for us, so that after we can just go to `http://{External_IP}`.

The packet path looks like this:
```
Client → Public IP → Azure LB → any node (VMSS) → kube-proxy iptables/IPVS → n8n pod :5678
```

Azure LB is L4. It just forwards TCP to a healthy node, and kube-proxy on that node routes the packet to a matching pod, even one on another node.

#### How it works under the hood?

Azure-side components:
- `VMs` or `VM Scale Set` - AKS nodes
- `VNet and subnet` - private network
- `Public IP` - internet reachable IP address
- `Azure Load Balancer` - forwards TCP/UDP packets
- `Network Security Group` - firewall attached to subnet or NIC
- `Node resource group (MC_...)` - a folder of Azure resources that AKS creates and manages for you.
- `Azure Resource Manager` - API through which everything in Azure is created
- `Manager identity` - identity to call Azure Resource Manager
Kubernetes-side components:
- `API-server and etcd` - API and database of resource allocation notes
- `EndpointSlice controller` - keeps a live list of the pod IPs that match a Service's selector.
- `kube-proxy` - runs on every node and turns Services into Linux kernel rules (iptables or IPVS)
- `cloud-controller-manager (CCM)` - the bridge between Kubernetes and Azure. In AKS it runs inside the control plane that Microsoft hosts, so you never see it.

Steps:
1. **kubectl** sends the Service YAML to the **API server**.
2. The **API server** saves it in **etcd** and assigns a ClusterIP and a NodePort.
3. The **EndpointSlice controller** finds the n8n pods and records their IPs.
4. **kube-proxy** on every node writes iptables rules: public IP / NodePort → pod IP:5678.
5. The **cloud-controller-manager** sees `type: LoadBalancer` and logs into **Azure ARM** with the **managed identity**.
6. **ARM** creates a **Public IP**.
7. **ARM** configures the **Azure Load Balancer**: frontend (public IP), backend pool (node VMs), health probe, and rule (port 80 → nodes).
8. **ARM** adds an **NSG** rule allowing port 80.
9. The **cloud-controller-manager** writes the public IP into the Service status, and kubectl shows the EXTERNAL-IP.


Links:

202611230951

