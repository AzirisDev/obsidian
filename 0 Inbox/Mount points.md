Mount point is a directory to which partition can be attached, so that its content becomes accessible.
In Linux, everything starts from root directory. Extra partitions should be mounted specifically.

Example:
We have two partitions:
- /dev/sda1 - contains OS
- /dev/sda2 - external USD drive
Mounting can look like that:
- /dev/sda1 is mounted on / -> system files
- /dev/sda2 is mounted on /mnt/usd/ -> usb content

Commands
- sudo mount /dev/sda1 /mnt/usb - mount 
- sudo umount /mnt/usb - unmount

To persitently mount certain partitions, tweak **/etc/fstab** file



Links:

202508272229

