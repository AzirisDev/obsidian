![[Screenshot 2026-09-29 at 23.48.39.png]]

## IP Addressing

|Subnet|Link|Left Device|Right Device|
|---|---|---|---|
|`10.1.1.0/24`|host1 -- srl1|host1: `eth1` = `10.1.1.2`|srl1: `e1-1` = `10.1.1.1`|
|`10.1.2.0/24`|srl1 -- srl2|srl1: `e1-2` = `10.1.2.1`|srl2: `e1-1` = `10.1.2.2`|
|`10.1.3.0/24`|srl1 -- srl3|srl1: `e1-3` = `10.1.3.1`|srl3: `e1-1` = `10.1.3.2`|
|`10.1.4.0/24`|srl2 -- host2|srl2: `e1-2` = `10.1.4.1`|host2: `eth1` = `10.1.4.2`|
|`10.1.5.0/24`|srl3 -- host3|srl3: `e1-2` = `10.1.5.1`|host3: `eth1` = `10.1.5.2`|
|`10.1.6.0/24`|srl2 -- srl3 (new)|srl2: `e1-3` = `10.1.6.1`|srl3: `e1-3` = `10.1.6.2`|

Convention: routers get `.1`, hosts get `.2`.

## BGP Design

|Router|ASN|Router-ID|Neighbors|
|---|---|---|---|
|srl1 (hub)|65001|10.0.0.1|srl2 (`10.1.2.2`, AS 65002), srl3 (`10.1.3.2`, AS 65003)|
|srl2 (spoke)|65002|10.0.0.2|srl1 (`10.1.2.1`, AS 65001), srl3 (`10.1.6.2`, AS 65003, after exercise 3)|
|srl3 (spoke)|65003|10.0.0.3|srl1 (`10.1.3.1`, AS 65001), srl2 (`10.1.6.1`, AS 65002, after exercise 3)|
Links:

202609292347

