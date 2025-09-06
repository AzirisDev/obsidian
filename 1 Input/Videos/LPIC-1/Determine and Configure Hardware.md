We have hardware: motherboard, ram cards, flash memories, etc. We have users and applications/programs. At the end, operating system is working like a bridge between these two, managing and allocating resources around.

Also, we have firmware. It is small software **on** the hardware that makes sure it runs.

When computer starts, it should be navigated first.
1) BIOS - Basic Input/Output system - old, redundant. It is text-based system that boots the computer, accessing the first sector of first partition - [[Master Boot Record(MBR)]] it is small
2) UEFI - Unified Extensible Firmware Interface - new. It uses separate partition and FAT. It is located at /boot/efi - it can be any size

PCI - Peripheral Component Interconnect - enables user to add extra components to mother board.
We can check them by "lspci" command.
We have also SSD, HDD, USB, GPIO (arduino type stuff)

[[Kernel provides sysfs to get information and configurations of the hardware]]
[[ls commands for hardware]]
[[Loadable Kernel modules are built-in in Linux]]




Links:

202509041002

