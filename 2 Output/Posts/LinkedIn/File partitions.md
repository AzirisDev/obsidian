Have you ever wondered how Linux actually handles files across different disks and devices?

It all comes down to **partitions and mount points**.

✅ A partition is a logical section of a physical disk. One disk can hold multiple partitions, each with its own file system.  
✅ We create partitions to separate operating systems, organize data, or improve security.  
✅ To access a partition, Linux uses a _mount point_ — a directory where that partition is attached.

Example:
1. `/dev/sda1` contains the OS, mounted at `/` → system files.
2. `/dev/sda2` is a USB drive, mounted at `/mnt/usb/` → USB content.

Useful commands:
- `sudo mount /dev/sda2 /mnt/usb` → mount a device.
- `sudo umount /mnt/usb` → unmount it.
- Persistent mounts are configured in `/etc/fstab`.

And it doesn’t stop at local disks. With **NFS (Network File System)**, you can mount remote file systems and directly access or edit files from other machines as if they were local.

Have you ever set up custom mount points or used NFS in your projects? I’d love to hear your experience 👇

Follow me for practical Linux and DevOps insights.

#Linux #DevOps #FileSystems #Kubernetes #CloudNative

![[Gemini_Generated_Image_244x11244x11244x.png]]