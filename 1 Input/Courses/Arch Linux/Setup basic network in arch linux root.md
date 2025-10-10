We will be setting up the network via `systemd & networkd & iwd`. 
- `systemctl enable systemd-networkd.service` - enable the network service
- `systemctl enable systemd-resolved.service` - enable resolved stuff to connect with DNS resolving
- `ip link` - get the network devices info
- create `/etc/systemd/network/25-wireless.network` and put that in it
```
[Match]
Name=wlp2s0

[Link]
RequiredForOnline=routable

[Network]
DHCP=yes
IgnoreCarrierLoss=3s
```
- `pacman -Syu iwd` - install wireless daemon
- `systemctl enable iwd.service` - enable the wireless network service
- `vim /etc/hostname` - set a hostname

Links:

202510101909

