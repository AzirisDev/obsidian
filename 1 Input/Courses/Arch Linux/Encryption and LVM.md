We use dm-crypt for encryption of disks inarch Linux. You can go here https://wiki.archlinux.org/title/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS. We use LVM on LUKS. It is simple to partition; only one key needed to open.

### Steps to create encrypted stuff
1) `cryptsetup luksFormat memory_block_name` - create the LUKS encrypted container at the designated partition
2) `cryptsetup open memory_block_name cryptlvm` - open container
3) `pvcreate /dev/mapper/cryptlvm` - create a physical volume on top of the opened LUKS container
4) `vgcreate MyVolGroup /dev/mapper/cryptlvm` - create a volume group  and add the previously created physical volume to it
5) `lvcreate -L 4G -n swap or root or home MyVolGroup` - create all your logical volumes on the volume group
6) ```
   mkfs.ext4 /dev/MyVolGroup/root
   mkfs.ext4 /dev/MyVolGroup/home
   mkswap /dev/MyVolGroup/swap
   ```
   Format your file systems on each logical volume.
7) ```
   mount /dev/MyVolGroup/root /mnt
   mount --mkdir /dev/MyVolGroup/home /mnt/home
   swapon /dev/MyVolGroup/swap
   ```
   Mount your logical volumes.
8) Prepare boot partition
	1) `mkfs.fat -F32 memory_block_name` - format file system
	2) `mount --mkdir memory_block_boot_name /mnt/boot` - mount the boot partition
9) Use `pacstrap` command to go to actual installation of Arch Linux.
		`pacstrap -K /mnt base linux linux-firmware`\
10) `fstab` - vital part in rebooting the system - configuration file that identifies how devices, blocks and other thing should be mounted during system boot.
	1) `genfstab -U /mnt >> /mnt/etc/fstab` - generates the fstab file
11) `arch-chroot /mnt` - start the root file system


Links:

202510081738

