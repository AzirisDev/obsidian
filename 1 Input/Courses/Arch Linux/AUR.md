Arch User Repositories. Not safe. Just users that create repositories and maintain them. 

We have _YAY_ - reads packages from AUR and builds them for you.

- `sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si` - download yay
- We will get the error. It is because of resolved.conf and mirrors.
- `ln -sf ../run/systemd/resolve/stub-resolv.conf /etc/resolv.conf` - we should run this. To provide [domain name resolution](https://wiki.archlinux.org/title/Domain_name_resolution "Domain name resolution") for software that reads `/etc/resolv.conf` directly, such as [web browsers](https://wiki.archlinux.org/title/Web_browsers "Web browsers"), [Go](https://wiki.archlinux.org/title/Go "Go"), [GnuPG](https://wiki.archlinux.org/title/GnuPG "GnuPG") and [QEMU](https://wiki.archlinux.org/title/QEMU "QEMU")when using user networking, _systemd-resolved_ has four different modes for handling the file—stub, static, uplink and foreign. They are described in [systemd-resolved(8) § /ETC/RESOLV.CONF](https://man.archlinux.org/man/systemd-resolved.8#/ETC/RESOLV.CONF). We will focus here only on the recommended mode, i.e. the stub mode which uses `/run/systemd/resolve/stub-resolv.conf`.`/run/systemd/resolve/stub-resolv.conf` contains the local stub `127.0.0.53` as the only DNS server and a list of search domains.

Links:

202510162157

