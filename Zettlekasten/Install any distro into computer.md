- Download .iso file of any distro.
- diskutil list - (if macos) find your USB driver
- diskutil unmountDisk /dev/your-driver - erase the content in it
- sudo dd if=path-to-your.iso of=/dev/your-driver bs=4M status=progress oflag=sync - make your USB driver bootable
- diskutil eject /dev/your-driver

[[Zettlekasten/How to start with Linux|How to start with Linux]]


Links:

202509091239

