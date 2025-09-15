GRUB is a smart multi-stage boot-loader. It runs MBR at one its part and then continues with other booting processes or even can chain boot other OS boot loader.

GRUBv1 is legacy. It is located at /boot/grub and its config is /boot/grub/menu.lst.
In modern system grub config is located at /boot/grub/grub.conf, but it is linked to /menu.lst.

### grub.conf

- it has many properties like set default="0"
- menu entry title {...}
	- set root = ... - specifies root partition
	- linux = ... - points to kernel file
	- initrd = ... - points to initramfs

It is better to edit grub configuration from here /etc/default/grub and run update-grub afterwards. 
- update-grub -> grub-mkconfig -o /boot/grub/grub.conf


### Booting from grub command-line

- linux (hd0,gpt2)/boot/vmlinuz-version root=location-of-partition
	- location-of-partition -> /dev/sda2  if it is SATA drive
	- location-of-partition -> /dev/nvme0n1p2 if it is NVMe drive
- initrd (hd0,gpt3)/boot/initrd.img-version
- boot

You can play around with configs and pass many parameters.




Links: [[Boot Loader]]

202509091458

