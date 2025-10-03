Hardware has NIC - Network Interface Card - it is used to be connected and work with network.
We can check the information using `ifconfig` command.
- ifconfig `device` IP-address `netmask` NetMask - change network config for time.

 `/etc/network/interfaces` has default configuration of network stuff in Debian machines.

Nowadays, people use `ip` command to work with network configuration.
```
ip link show # shows links to the outside world
ip addr add 172.19.1.10/24 dev eth2 # temporary adding an IP
ip addr show eth2
ip addr del 172.19.1.10/24 dev eth2 # deleting an IP address
ip link set eth2 up # brining a NIC up
ip route show
ip route add default via 192.168.1.1 # add default gateway
```

Linux has service named Network Manager and `nmcli` as tool to speak to it. It is a service that manages all the things that is dealing with network stuff, wifi, ethernet, etc.

Hostname - name of IP addresses like `tiger.local` -> `192.168.1.1`.
- hostname - check your hostname
- hostnamectl set-hostname new_name
`/etc/hosts` contains hostnames for every server that you work with in your computer.
Links:

202510031600

