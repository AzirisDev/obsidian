Before installing any system, a smart engineer designs the disk layout first.

Here’s a simple, reliable structure you can apply right now:

✅ **/boot** – 100 MB is usually enough, this partition stores the bootloader and must stay unencrypted.  
✅ **/** (root) – holds your operating system and all core directories like `/bin`, `/etc`, `/lib`, and `/usr`.  
✅ **/home** – keeps user data separate from the OS, making upgrades or recovery painless.  
✅ **/swap** – used when RAM runs out, typically equal to RAM + 2 GB for modern systems.

Optional but useful:
1. **/var** – store logs separately to prevent log floods from filling up your system.
2. **/srv** or **/opt** – isolate service data or third-party applications.

The goal isn’t just to “install Linux”. It’s to design a system that’s stable, maintainable, and secure.

What’s your go-to disk layout when setting up new Linux servers? Let’s compare setups 👇

Follow me for more practical DevOps and Linux insights.

#Linux #DevOps #SysAdmin #CloudNative #ServerDesign

![[Gemini_Generated_Image_d7gkoyd7gkoyd7gk.png]]