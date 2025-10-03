We have private and public IPs. If you have homelab, you can use following IP range to assign:
```
|192.168.0-255.0-255|65K IPs|
|172.16-31.0-255.0-255|1M IPs|
|10.0-255.0-255.0-255|16M IPs|
```

How router understands where to send the information, which IP address. For example, you use `192.168.1.*` format. We have CIDR notation - netmask - `255.255.255.0`, it checks first 3 octets of address and identifies where to send it to private IP or global IP.

#### Communication Protocols & Ports
How data is transferred.
- TCP - send information without loosing any data
- UDP - it is much faster, but can lose some data
- ICMP - check connectivity to the servers; `ping` command

Each service on the machine will have its own port assigned, just to grab information. It is better to assign your own services port number larger than 1024 - 64000. Also, you can check that info in `/etc/services`.

Links: [[Network operations]] 

202510031312

