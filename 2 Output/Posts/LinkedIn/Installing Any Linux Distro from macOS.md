Ever tried installing Linux from macOS and got lost halfway?  
Here’s a simple way to make your USB bootable the right way 👇

1. Download the `.iso` file of your preferred distro.
2. Run `diskutil list` to find your USB drive.
3. Unmount it using `diskutil unmountDisk /dev/your-driver`.
4. Flash the ISO with:  
    `sudo dd if=path-to-your.iso of=/dev/your-driver bs=4M status=progress oflag=sync`
5. Finally, eject it with `diskutil eject /dev/your-driver`.
    

That’s it. Your USB is now bootable and ready to install Linux anywhere.  
Just remember, **`dd` doesn’t forgive typos**, so double-check your drive name before hitting Enter.

What distro was your very first install, and how did it go? 👇  
Follow me for practical Linux and DevOps insights.

#Linux #DevOps #OpenSource #SysAdmin #CloudNative

![[Gemini_Generated_Image_ugm3txugm3txugm3.png]]