[[File partition]]

The partitions of disk usually located at "/dev". There are might be /dev/sda, /dev/hdc, /dev/nvme0. etc. We recognize them as: - /dev/sd**a**1 (first partition of the first SCSI disk) - /dev/hd**b**3.

BIOS systems were having only 4 partitions at all. But we can make more partitions using logical partitions, by dividing last 4th partitions into more partitions and et cetera.

- `/dev/sda3` is the 3rd primary partition on the first disk
- `/dev/sdb5` is the first logical partition on the second disk
- `/dev/sda7` is the 3rd logical partition of the first physical disk

UEFI systems can make up to 128 partitions.

#### Commands for partitions:
- fdisk partition - we have here many commands to view, extend, separate, etc
- gparted - graphical tool to manage partitions

### LVM - Logical Volume Manager
It is used to manage all memory that you have, as flexible as you want. For example, you have 2 separate Physical Volumes of 2 GB - disks. But you want to allocate 3GB to one partition. So LVM will combine two disks into one Volume Group and partition it as you want.



Links:

202509081058

