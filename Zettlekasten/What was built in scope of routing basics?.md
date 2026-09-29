What is going to be build:![[Screenshot 2026-09-29 at 13.28.07.png]]

 - `IP label convention` - Routers get `.1` on host LANs and hosts get `.2`. On router-to-router links, the hub is `.1` and the spoke is `.2`.
 - **Why does each host's config delete the default route before adding a new one?**  Docker gives every container a default route via `eth0, the management network`. If it stayed, host1's pings to `10.1.4.2` would leave through Docker's bridge instead of through srl1. Replacing it with a default via the router's `.1` forces traffic into the lab.


Links:

202609291424

