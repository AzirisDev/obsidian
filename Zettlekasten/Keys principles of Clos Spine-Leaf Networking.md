Key design principles:

- **/31 point-to-point links** between each spine-leaf pair (no wasted IPs)
- **RFC 7938 eBGP with shared spine ASN** -- both spines share AS 65000, leaves get unique ASNs 65001-65004
- **peer-group** configuration groups neighbors with common policy (all leaves on a spine share one peer-group, all spines on a leaf share another)
- **router-ID** is a unique loopback-style address per device (10.0.1.x for spines, 10.0.2.x for leaves)
- **No oversubscription between tiers** -- aggregate leaf uplink bandwidth equals spine capacity
- **ECMP across spines** -- traffic between any two leaves is load-balanced across all available spines

Links:

202610011302

