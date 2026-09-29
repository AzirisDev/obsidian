![[Screenshot 2026-09-23 at 16.43.47.png]]

Usually we merge L5-L7. The core idea is encapsulation. Each layer is wrapping the object into its own header and pass down.

- `Applciation Layer` - HTTP status codes, DNS resolution, TLS certificates. This is where we have nginx, ingress controllers and API Gateways. Here we have URLs and hostnames
- `Transport Layer` - TCP and UDP protocols, ports. We mostly have security groups and firewall work here. 
	-  -> Which application on that host should get this data, and does it need to arrive reliably and in order?
- `Network Layer` - IP addressing, subnetting, routing tables, NAT. 
	- -> Where is the final destination, and which path gets me there across multiple networks? Which network I am in?
- `Data link` - MAC Addresses, ARP, VLANs. Bridges in docker, switches and k8s networking is here. 
	- -> Who is the next device on my local network, and how do I deliver this frame to it without errors?
- `Physical` - veth paris, real cable, Network Interface Cards. 
	- -> is internet connected? Is everything UP?

Links:

202609231639

