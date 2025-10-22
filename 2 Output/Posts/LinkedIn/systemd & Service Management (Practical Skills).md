If you manage Linux systems daily, mastering `systemd` isn’t optional.

It’s the heart of modern service management — but most engineers only know 3 commands.

Here’s how to take control of your system like a pro:

✅ Use `systemctl list-units` to see everything systemd controls.  
✅ Check only targets with `systemctl list-units --type=target`.  
✅ Start, stop, or restart services like `sshd` using `systemctl start|stop|restart sshd`.  
✅ Enable or disable services on boot with `systemctl enable|disable sshd`.  
✅ Investigate logs using `journalctl -u sshd` or kernel logs with `journalctl -k`.

Pro tips:  
• Reload configuration files with `systemctl reload sshd`.  
• Run `systemctl daemon-reload` after editing systemd unit files.  
• Check if your system is healthy with `systemctl is-system-running`.

Once you master `systemd`, Linux stops being a mystery — it becomes predictable and controllable.

What’s your go-to systemd command you use daily? Share it below, maybe someone will learn a new trick 👇

Follow me for hands-on Linux and DevOps knowledge.

#DevOps #Linux #Systemd #CloudNative #SRE

![[ChatGPT Image Oct 22, 2025 at 06_00_18 PM.png]]