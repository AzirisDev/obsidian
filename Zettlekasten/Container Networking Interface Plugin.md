It is specification and set of plugins that assigns IP addresses to pods, sets up routes and establish communication between pods.
`Kubelet` calls `CNI` when pod is created to set it all up and connect it to pods, services, external networks.

There are several CNIs out there:
- `Cilium`
- `Calico`
- `Flannel` 

#### How to identify which CNI cluster uses?
- `rdctl shell bash` - enter rancher desktop VM
- `cd /etc/cni` - go to CNI directory
- `vim net.d` - here you can see necessary info
  
 
Links:

202609111212

