- `IP table`- list in each router with destination networks and where to send packets. If there is no match -> goes to `default route` -> drops. 
- Router cares only `destination IP`. Routing table contains `prefix` - destination network, `next_hop` - IP to route the packet
- It works by `longest prefix match`. For example:
```
|Prefix|Next hop|
|---|---|
|0.0.0.0/0|10.0.0.1 (default route)|
|192.168.10.128/25|10.0.0.4|
```
	A packet is going to **192.168.10.200**. It matches all four entries:
	- /0 matches everything
	- /25 matches because 200 falls in 128–255
	The router chooses /25 → 10.0.0.4, since 25 bits is the longest match.
- `Directly connected route` - a route created automatically when you configure an IP on an interface. When srl1 gets `10.1.1.1/24` on e1-1, it instantly knows `10.1.1.0/24` is reachable through e1-1. No next-hop is needed because the destination is on the wire.
- `Static route` - a route an administrator configures by hand: "to reach prefix X, send to next-hop Y." They're simple and predictable, and fine for small networks. But they don't adapt when a link fails, and they don't scale: many routers means a huge number of routes to maintain by hand.

Links:

202609291422

