![[Screenshot 2026-10-01 at 16.48.03.png]]
## IP Addressing
### Spine-Leaf Links (/31 point-to-point)

|Link|Subnet|Spine IP|Leaf IP|
|---|---|---|---|
|spine1 -- leaf1|`10.10.1.0/31`|`10.10.1.0`|`10.10.1.1`|
|spine1 -- leaf2|`10.10.1.2/31`|`10.10.1.2`|`10.10.1.3`|
|spine1 -- leaf3|`10.10.1.4/31`|`10.10.1.4`|`10.10.1.5`|
|spine1 -- leaf4|`10.10.1.6/31`|`10.10.1.6`|`10.10.1.7`|
|spine2 -- leaf1|`10.10.2.0/31`|`10.10.2.0`|`10.10.2.1`|
|spine2 -- leaf2|`10.10.2.2/31`|`10.10.2.2`|`10.10.2.3`|
|spine2 -- leaf3|`10.10.2.4/31`|`10.10.2.4`|`10.10.2.5`|
|spine2 -- leaf4|`10.10.2.6/31`|`10.10.2.6`|`10.10.2.7`|
### Host Subnets

|Leaf|Host Subnet|Leaf IP|Host IP|
|---|---|---|---|
|leaf1|`10.20.1.0/24`|`10.20.1.1`|`10.20.1.2`|
|leaf2|`10.20.2.0/24`|`10.20.2.1`|`10.20.2.2`|
|leaf3|`10.20.3.0/24`|`10.20.3.1`|`10.20.3.2`|
|leaf4|`10.20.4.0/24`|`10.20.4.1`|`10.20.4.2`|

Convention: routers get `.1`, hosts get `.2`.
## BGP Design

|Device|ASN|Router-ID|Peer Group|Neighbors|
|---|---|---|---|---|
|spine1|65000|10.0.1.1|leaves|leaf1 (`10.10.1.1`), leaf2 (`10.10.1.3`), leaf3 (`10.10.1.5`), leaf4 (`10.10.1.7`)|
|spine2|65000|10.0.1.2|leaves|leaf1 (`10.10.2.1`), leaf2 (`10.10.2.3`), leaf3 (`10.10.2.5`), leaf4 (`10.10.2.7`)|
|leaf1|65001|10.0.2.1|spines|spine1 (`10.10.1.0`), spine2 (`10.10.2.0`)|
|leaf2|65002|10.0.2.2|spines|spine1 (`10.10.1.2`), spine2 (`10.10.2.2`)|
|leaf3|65003|10.0.2.3|spines|spine1 (`10.10.1.4`), spine2 (`10.10.2.4`)|
|leaf4|65004|10.0.2.4|spines|spine1 (`10.10.1.6`), spine2 (`10.10.2.6`)|

Total unique BGP sessions: 8 (4 leaves x 2 spines)
### Routing Policies

The gNMIc config files create three policies chained as `["export-connected", "export-bgp"]` with `import-all`:

|Policy|Match|Default Action|Purpose|
|---|---|---|---|
|`import-all`|--|accept|Accept all routes from peers|
|`export-connected`|protocol local + prefix-set `host-subnets`|next-policy|Advertise connected host /24 subnets only|
|`export-bgp`|protocol bgp|reject|Re-advertise BGP-learned routes|

A `host-subnets` prefix-set (`10.20.0.0/16 mask-length-range 24..24`) on `export-connected` filters out /31 fabric link prefixes -- only host subnets belong in BGP. The /31 links are already known via direct connection on each router.
### BGP Multipath (ECMP)

SR Linux defaults to a single best path per prefix (`maximum-paths: 1`). To enable ECMP across spines, each router's `ipv4-unicast`address family sets `multipath maximum-paths` to allow multiple equal-cost next-hops:

- **Leaves:** `maximum-paths: 2` (one path per spine)
- **Spines:** `maximum-paths: 4` (one path per leaf)
- 
Links:

202610011647

