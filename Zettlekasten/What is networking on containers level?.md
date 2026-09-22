

>`Network namespace` is one of the type of general linux namespace, which is responsible for only networking. Isolation logic but in networking.

>`veth pairs` is virtual ethernet cable: we connect one end to the container, other end to the bridge.

>`bridge(docker0)` is virtual switch. Thanks to bridge connected containers can talk to each other and talk to internet via configured NAT. 

>`NAT - Network Address Translation` is method used by routers aka switch to let multiple devices in local network share one public IP address.

Links:

202609221255

