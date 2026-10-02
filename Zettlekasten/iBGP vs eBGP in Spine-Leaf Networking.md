iBGP uses same AS - Autonomous Systems - everywhere. But in here each router *will not* re-advertise what it learned from other peers. 
eBGP avoids the problem entirely. When every link is an eBGP session between different autonomous systems, every router re-advertises routes naturally.

We have RFC - Request For Comment - is documents in internet that is published and polished with many people around the world. RFC 7938 - document that tells how large-scale data-centers use BGP.
	`Main recommendation: use eBGP-only, with shared ASN across spines and unique ASN per leaf.`

Unique ASN across spines prevents loop during BGP UPDATE messages that send prefix being announced, AS-path it traveled and next hop to send traffic to.
Links:

202610011222

