There are many spheres of security. We will now setup _uncomplicated firewall_. Uncomplicated firewall is a program for managing firewall and provides a command line interface.

- `sudo pacman -Syu ufw`
- `systemctl enable ufw.service`
- `systemctl start ufw.service`

Lets configure firewall now:
- `ufw default deny` - it denies by default any protocol
- `ufw allow from 192.168.0.0/16` - allow any protocol inside my local network
- `ufw enable` - start firewall
- `ufw status` - check firewall state

Also lets install _arch-audit_ - check for vulnerabilities affecting running system.
- `sudo pacman -Syu arch-audit`
  
Links:

202510172006

