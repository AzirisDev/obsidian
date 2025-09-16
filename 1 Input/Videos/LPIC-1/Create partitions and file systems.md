#### Partitions
We have two types of partition tables: MBR and GPT. First one is for old machines and we use `fdisk` to works with them, other is new and `gdisk` for it.

`lsblock` gives info about all memory points.
`parted` gives opportunity to resize partitions. `gparted` is GUI to do it on UI.

With `fdisk or gdisk` we can create, delete, change type, print, list, toggle bootable, verify, write the partitions. You can use `m` to see the menu and work with them.

#### File systems
File system, a map of files to physical memory units, is needed to works and manage files.
We have certain types of file systems:
- ext family:
	- ext2 - old, do not have journaling - what I am doing now
	- ext3 - has journaling, 2TB - max file size, 16 TB - max file system size
	- ext4 - 16TB - max file size, 1EB - max file system size
- XFS - caches to RAM; good for uninterruptable work 
- Swap
- FAT family:
	- originally used for DOS and Windows
	- vFAT - FAT32 - old, lacks everything
	- extFAT - newer with big sizes
- btrfs - B-tree file system
	- work with volumes, look at the LVM at [[partitions]]

Commands:
- mkfs -t [type] /dev/[partition] - create file system in partition
- mkswap /dev/[partition]

Each partition has UUID, it is needed when you change your machine.
Links: [[partitions]] [[File partition]] 

202509161541

