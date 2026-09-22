```
1. Create two network namespaces:
    sudo ip netns add red
    sudo ip netns add blue
2. Verify they exist:
    sudo ip netns list
3. Create a Linux bridge and assign it an IP:
    sudo ip link add br-study type bridge
    sudo ip link set br-study up
    sudo ip addr add 10.0.0.254/24 dev br-study
4. Create veth pairs and wire up the "red" namespace:
    sudo ip link add veth-r type veth peer name veth-r-br
    sudo ip link set veth-r netns red
    sudo ip link set veth-r-br master br-study
    sudo ip link set veth-r-br up
5. Create veth pairs and wire up the "blue" namespace:
    same as above but with blue
6. Configure IPs and bring interfaces up inside each namespace (but **not** the loopback yet):
    # Red
    sudo ip netns exec red ip addr add 10.0.0.1/24 dev veth-r
    sudo ip netns exec red ip link set veth-r up
    
    # Blue
    sudo ip netns exec blue ip addr add 10.0.0.2/24 dev veth-b
    sudo ip netns exec blue ip link set veth-b up
    ```
7. Test connectivity between namespaces:
    # Red to blue
    sudo ip netns exec red ping -c 3 10.0.0.2
    
    # Blue to red
    sudo ip netns exec blue ping -c 3 10.0.0.1
    
    # Either namespace to the bridge gateway
    sudo ip netns exec red ping -c 2 10.0.0.254
    ```
8. Now try pinging the loopback address inside a namespace:
    sudo ip netns exec red ping -c 2 127.0.0.1

    It fails. Why? The loopback interface (`lo`) starts in a DOWN state in new namespaces.
    
9. Bring up the loopback in both namespaces and verify:
    sudo ip netns exec red ip link set lo up
    sudo ip netns exec blue ip link set lo up
    sudo ip netns exec red ping -c 2 127.0.0.1
```

Several things to mention:
- `lo - loopback interface` is DOWN by default. That is why `127.0.0.1` was unreachable
- it is no different from thing that we did in [[Networking lab00 - docker demo code & architecture]], we just did each step by ourselves.

Links:

202609221339

