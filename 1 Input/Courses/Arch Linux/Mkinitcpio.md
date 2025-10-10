This creates an initial ram disk environment. It sets up modules of kernel before hand over to init process and system boot. To configure that, we need to edit `/etc/mkinitcpio.conf`.
`HOOKS=(base systemd autodetect microcode modconf kms keyboard sd-vconsole block sd-encrypt lvm2 filesystems fsck)`
Now we need to regenerate that file: `mkinitcpio -P`.

We will encounter with some `vconsole` file. In order to overcome that we increase the default font size of console.
- `vim /etc/vconsole.conf`  and put there `FONT=latarcyrheb-sun32`

Now we have trouble with `pdata-tools`.
We missed `lvm2` package. Run `pacman -Syu lvm2`.

Rerun `mkinitcpio -P`. 


Links:

202510101929

