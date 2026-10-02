`BGP` runs the internet. Data centers, cloud networking, kubernetes networking.
`Autonomous Systems - AS` collection of IP addresses that belongs to one organization/network that presents one routing policy. `ASN` - unique number that identifies `AS`.
#### Examples
- AS15169: Google
- AS16509: Amazon (AWS)
- AS13335: Cloudflare
- AS8075: Microsoft

#### BGP peers goes through a state machine before exchanging routes:
```
|Idle|Not trying to connect|
|Connect|TCP connection in progress|
|OpenSent|TCP connected, OPEN message sent|
|OpenConfirm|OPEN received, waiting for KEEPALIVE|
|Active|Actively tries to restart or retry the TCP connection to the peer|
|Established|Peers are up, exchanging routes|
```
We need only `Established`, otherwise there no way to exchange routes.


#### Routing policies
1) `Import policies` - which routes to accept into route table; without any route is rejected
2) `Export policies` - which route to share to peers; without no route shared

In this lab, we use three policies chained together:

| Policy             | Purpose                              | Default Action |
| ------------------ | ------------------------------------ | -------------- |
| `import-all`       | Accept all received routes           | accept         |
| `export-connected` | Advertise directly connected subnets | next-policy    |
| `export-bgp`       | Re-advertise BGP-learned routes      | reject         |

**Policy chaining:** When a peer-group has multiple export policies (`[export-connected, export-bgp]`), SR Linux evaluates them in order. If a route matches a statement with `accept`, it's advertised. If it doesn't match any statement and the default-action is `next-policy`, it passes to the next policy in the chain. If the default-action is `reject`, the route is dropped. This lets you build modular, composable policies instead of one monolithic rule set.

#### BGP Best Path Algorithm

When a router receives the same prefix from multiple peers, BGP uses a decision process to select the best path. The simplified algorithm (in order of priority):

|Step|Attribute|Rule|In This Lab|
|---|---|---|---|
|1|Local Preference|Highest wins|Not set (default 100)|
|2|AS Path Length|Shortest wins|Exercise 2 demonstrates this|
|3|Origin|IGP (i) > EGP (e) > incomplete (?)|All routes are IGP|
|4|MED|Lowest wins (from same neighbor AS)|Not set|
|5|eBGP vs iBGP|eBGP preferred|All peers are eBGP|
|6|Router ID|Lowest wins (tiebreaker)|Only used if everything else ties|

In Exercise 2, when srl2 receives 10.1.5.0/24 from both srl1 (AS path: [65001, 65003]) and srl3 (AS path: [65003]), steps 1, 3, 4, and 5 are equal. Step 2 breaks the tie -- the direct path through srl3 has a shorter AS path (1 hop vs 2 hops), so BGP selects it automatically.

Links:

202609292245

