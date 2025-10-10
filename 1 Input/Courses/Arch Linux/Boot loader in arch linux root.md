Lets use systemd-boot for boot loader. Make sure that partition is `EFI mode` and mounted in `/boot`.

- `bootctl install` 

Now we need to configure the boot loader entries.
- `cd /boot` and check the files. Here we can see `initramfs-linux.img and xmlinuz-linux`. Those needed to start the system.
- `cd loader/entries` and create `arch.conf`. Put in the file the pointer:
	- `blkid` - get UUID of devices and insert the UUID of main memory device here and also change the name of it
```
title Arch Linux
linux /vmlinuz-linux
initrd /initramfs-linux.img

options rd.luks.name=<device-UUID>=volumegroup root=/dev/volumegroup/root rw 
```

Now create the user, also make it a root user.
- `useradd azim`
- `usermod -aG wheel azim` - add azim to wheel group, which is kinda root user
- `visudo` and uncomment wheel group
- `passwd` - set the root password
- `passwd azim` - set the users password

Remove the USB and reboot. Login and you are ready to go. Connect to wifi. Download `pacman -Syu curl openssh bash-completion` , `systemctl enable sshd.service & systemctl enable sshd.service`  to be able to ssh to that computer. 

DONE! You can boot your computer.

Links:

202510101952

