Azure runs the `control plane` with API server, etcd, scheduler, controller manager, and we manage the `worker nodes`. Azure handles upgrades, availability, certificates. For that we pay and also we pay for VMs with resources.

`SLA` - Service Level Agreement - promise about uptime and other things.
#### Core concepts
1) `Cluster modes`: AKS Standard and AKS Automatic. On later, Azure setup settings on certain things
2) `Pricing`: The _Free_ tier has no SLA and suits learning. _Standard_ adds an uptime SLA and supports larger clusters. _Premium_ adds long-term support for Kubernetes versions.
3) `Node pools`: Nodes are grouped into pools, and each pool is backed by a Virtual Machine Scale Set. A _system_ pool runs critical pods like CoreDNS and metrics-server. _User_ pools run your workloads.
4) `Availability zones`: we have to understand that resource transfer between zones are hard/impossible, just remember
5) `Node resource group`: AKS creates a second resource group, named `MC_<rg>_<cluster>_<region>`, which holds the VMs, disks, load balancer, and public IPs. Don’t edit resources there by hand.
6) `Networking`: The main options are:
- **Azure CNI Overlay**, the common modern default, where pods get IPs from a private overlay range. It creates virtual networks so IP addresses can go on
- **Azure CNI (flat)**, where pods get real VNet IPs.
- **Azure CNI powered by Cilium**, which uses eBPF dataplane and network policy. 
You also choose between a public and a private API server, and between Azure Network Policy, Calico, or Cilium for network policies.
	Choose `CNI Overlay`, check `Cilium usage`for testing
1) `Identity`
- The cluster itself uses a managed identity.
- Users authenticate through Microsoft Entra ID, optionally with Azure RBAC for Kubernetes authorization.
- Pods access Azure resources such as Key Vault or Storage through **Workload Identity**, with no secrets stored in the cluster.
	Uncheck `Workload Identity` and `OIDC` for testing
1) `Integrations`: AKS connects to Azure Container Registry (ACR) for images, Key Vault (via the CSI driver), Azure Disks and Files for persistent volumes, Azure Monitor, Managed Prometheus, and Managed Grafana.

[[Kubectl shows k3s instead of AKS after az aks get-credentials]]
[[AKS with Terraform]]


Links:

202611201552

