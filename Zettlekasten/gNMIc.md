gNMI collector - CLI client for `gNMI, the gRPC-based protocol from OpenConfig`. 

What it does that `Ansible` can't?
Ansible is great for configuration automation. Ansible only knows what's happening at the moment it runs. It pushes config, maybe checks that the push succeeded, and exits. But the whole point of BGP is that things change after Ansible is gone. A link flaps at 3 a.m., a neighbor goes down, a route disappears, an interface starts dropping packets. Ansible has no idea, because it isn't running. Your config is still correct, but your network is broken.

That's the gap monitoring fills. Config tells you what you told the network to do. Telemetry tells you what the network is actually doing right now. `gnmic` is the piece that collects that second part.



Links:

202609292321

