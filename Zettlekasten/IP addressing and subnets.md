IP address has two part: `network part` and `host part`.

- `10.1.1.2 / 24` 
	- `block size` - 8 bits per each part, 32 - 24 = 8 -> 2^8 = `256`
	- `network IP` - highest multiplier of `256` under `10.1.1.2` -> 0 -> `10.1.1.0`
	- `broadcast IP` - `network IP` + `block size` - 1
	- `available hosts range` - everything between `network IP` and `broadcast IP`


 If two IPs share the same network portion, they can communicate directly at Layer 2 (via ARP + MAC). If they don't, traffic must go through a router at Layer 3.

Here we have such thing as ARP - Address Resolution Protocol

ARP gets MAC address, wraps it into frame and connects it with IP address, only thing that is available for application. How it happens by steps:
1) Checks ARP table - cache might be empty
2) It broadcasts to everyone in local network: "Who has 10.1.1.1? Reply me - 10.1.1.5"
3) The device that owns 10.1.1.1 replies directly: "10.1.1.1 is at `aa:bb:cc:dd:ee:ff`."
4) Your host saves that mapping in its ARP table for a while and builds the frame.

`ip neigh` - get ARP table

Links:

202609231757

