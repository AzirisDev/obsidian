Boot process:
1) Firmware does POST - Power On Self Test
2) Motherboard loads [[Boot Loader]]
3) Boot Loader loads Linux Kernel with its configs
4) It runs [[init program]]
5) Kernel loads and prepares a system to start and runs initramfs (we have startup drivers in it)
6) Init program starts necessart programs like networking, webserver, etc

Firmware can be [[BIOS]] or UEFI. [[Determine and Configure Hardware]]

Boot loader initializes minimal hardware necessary to boot the system. It is GRUB.

Kernel - core of OS. It needs initial drivers in initramfs to boot. You can send paramteres via GRUB configs during boot process.

[[Theere is a tool to read kernel level messages - dmesg]]

[[systemd let us runs services]]




Links: [[Linux boot process]]

202509050819

