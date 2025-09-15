**Day 1**  
Most devs treat the **Linux boot process** as a black box.  
But every time you hit power, a hidden sequence transforms hardware into a running system.  
Understanding it means you stop being just a _user_ and start thinking like an engineer.

---

**Day 2**  
Step 1 of Linux boot: **BIOS**.  
It wakes up the hardware, checks memory, and prepares the system for what comes next.  
The entire chain of boot steps rests on this tiny piece of firmware.

---

**Day 3**  
**MBR + Boot Loader** are the unsung heroes of Linux boot.  
🔹 MBR stores the partition table and points to the Boot Loader.  
🔹 Boot Loader loads the OS into RAM and hands control to the Kernel.  
Without them, your OS would never even start.

---

**Day 4**  
From **Initramfs → Kernel → systemd**:  
✅ Initramfs loads drivers and tools.  
✅ Kernel configures hardware and memory.  
✅ systemd launches services and keeps dependencies in order.  
That’s how Linux goes from bare metal to a GUI.