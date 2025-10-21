https://www.net.in.tum.de/fileadmin/TUM/NET/NET-2024-04-1/NET-2024-04-1_16.pdf
Interesting work. Article is about journey of a network packet in Linux kernel starting from network card till application/socket.

We have two paths: ingress - receiving packets, egress - sending packets. Packets are wrapped into _sk_buffer_ - it is a C language structure. It contains metadata and pointers to memory. It is very efficient as it works only with pointers for modification and etc.

We have following layers:
```
[App/User Space]
     ↓ ↑
+-------------------+
|   Socket API      | ←→ e.g. curl, nginx, ping, SSH
+-------------------+
     ↓ ↑
| Transport Layer   | (TCP, UDP)
     ↓ ↑
| Network Layer     | (IP, routing)
     ↓ ↑
| Netfilter / QoS   | (iptables, nftables, tc)
     ↓ ↑
| Device Layer      | (drivers, NIC queues)
     ↓ ↑
[Hardware: Network Card]
```

1) Any application uses socket API via nginx, curl or whatever to send/receive information.
2) Here we choose between reliability (TCP) or streaming preferences (UDP)
3) IP addressing, routing, fragmentation happens here. Packet wrapped with IP information.
4) Optional layer to setup security stuff like firewall or traffic control. 
5) Network Interface card manages packets using ring buffer.



Links:

202510211123

