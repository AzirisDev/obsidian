[[Why do we need dynamic routing?]]

In dynamic routing we need protocol to make it work. Here [[BGP - Border Gateway Protocol - fundamentals]] comes.

In Lessons 2-3, we used `Ansible` with `JSON-RPC` to configure routers. [[gNMIc]] takes a different approach: it speaks `gNMI (gRPC Network Management Interface)`, a model-driven protocol based on `YANG` data models.

[[What was build during dynamic routing & BGP?]]

Lessons learned:
- We were pinging from host1 -> host3. During that we disabled connection between them. But `dynamic routing` adapts to failures. The network healed itself. When the direct link went down, `BGP` found an alternate path through the triangle. When the link came back, `BGP` preferred the shorter path again. No human intervention was needed at any point.
	`TTL` - means IP packet header that limits how many hops (routers) a packet can pass through before being discarded
- Both sides must agree on AS numbers. When debugging BGP, check session state first. If a session is stuck in `active` or `connect`, the most likely causes are: wrong peer-as, wrong peer-address, or a firewall blocking TCP port 179. The `active` state specifically suggests the TCP connection succeeds but the OPEN message is rejected -- which points to an AS number mismatch.
- We have different route sources: local/connected, static, BGP. They have decreasing priority. In exercise, we override the route with wrong one. 10.1.4.0/24 shows `static` with next-hop 10.1.3.2 (srl3). But host2 is behind srl2, not srl3. The correct next-hop should be 10.1.2.2. BGP knows this -- but the static route wins. The diagnostic clue is a mismatch between received and active route counts in the BGP neighbor table.

Links: https://github.com/drewelliott/kubecraft/tree/main/lessons/clab/04-dynamic-routing-bgp

202609292117

