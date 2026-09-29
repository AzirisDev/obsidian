Key lessons: 
- A missing route on any router in the path (including the return path) breaks connectivity. The failure is not always obvious -- the forward direction might work fine while the return silently fails. Always trace both directions when debugging.
- A routing table entry is just data -- the router trusts it completely. If the data is wrong, traffic disappears into a black hole. The routing table says the route is valid, but the forwarding plane cannot deliver. Always verify that next-hops are reachable at Layer 2, not just that routes exist in the table.
- What happens during route looping problem? **TTL (Time To Live):** Every IP packet carries a TTL field (set to 64 by default on Linux). Each router that forwards the packet decrements the TTL by 1. When the TTL reaches 0, the router drops the packet and sends an ICMP "Time Exceeded" message back to the sender. This is what prevents routing loops from consuming network resources forever. Without TTL, a looping packet would circulate until the link saturated. `traceroute -n -w 2 10.1.5.2`
- A route in the routing table is a forwarding instruction, not a guarantee. The route says "send to 10.1.3.2 via ethernet-1/3" but if ethernet-1/3 is down, the instruction cannot be executed. Route existence does not equal path availability. This is a major limitation of static routes compared to dynamic routing protocols, which automatically adapt to topology changes.

Links:

202609291620

