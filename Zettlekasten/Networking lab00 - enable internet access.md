```
1. First, find your host's outbound interface:
    ip route show default

    Note the interface name after `dev` (e.g., `enp6s0`, `enp0s3`, `wlan0`). On modern Linux this is not `eth0` -- use whatever your system shows.
    
2. Add default routes in each namespace so they send non-local traffic to the bridge:
    sudo ip netns exec red ip route add default via 10.0.0.254
    sudo ip netns exec blue ip route add default via 10.0.0.254
3. Enable IP forwarding on the host:
    sudo sysctl -w net.ipv4.ip_forward=1
4. Allow forwarding for br-study. Docker sets the FORWARD chain policy to DROP, which blocks our traffic:
    sudo iptables -A FORWARD -i br-study -j ACCEPT
    sudo iptables -A FORWARD -o br-study -j ACCEPT
5. Add a masquerade rule (replace `enp6s0` with your actual interface from step 1):
    sudo iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o enp6s0 -j MASQUERADE
6. Test internet access from the namespaces:
    sudo ip netns exec red ping -c 3 8.8.8.8
    sudo ip netns exec blue ping -c 3 1.1.1.1
7. Inspect Docker's own NAT rules for comparison:
    sudo iptables -t nat -L POSTROUTING -v
```

Several new things to mention:
- `default route` - routes any request that is not within existing routes navigates to `default` one
- at 3 step, we making linux the serve not as just host, but also as a `router`. 
- `Masquerade` happens at the last step before sending request to internet. Ping from `10.0.0.1` to `8.8.8.8` should return back. By rewriting the source to the host's real IP (say `192.168.1.50`), replies come back to the host, and the kernel's **connection tracking (conntrack)** remembers the mapping so it can rewrite the destination back to `10.0.0.1` on the way in.


- Second line is what we set manually on `step 5`, masquerading your namespace subnet `10.0.0.0/24` out the real NIC
- First line: Masquerade any packet **from** `172.17.0.0/16` (Docker's default bridge subnet) going **out any interface except `docker0`** (that's what the `!docker0` means — the `!` is negation). So: containers talking to the outside world get NAT'd; containers talking to each other stay on `docker0` and are skipped, because inter-container traffic doesn't need NAT.![[Screenshot 2026-09-22 at 15.49.19.png]]
Links:

202609221417

