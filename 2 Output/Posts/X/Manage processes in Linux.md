**Tweet 1 (Day 1)**  
💻 Every DevOps engineer asks: _How do I manage processes in Linux?_  
It starts with **priority**:  
⚡ `nice` → sets process priority (-20 high, 19 low)  
⚡ `renice` → adjust priority later (root can raise it)  
Master these, and you control who gets CPU time.  
#Linux #DevOps

---

**Tweet 2 (Day 2)**  
Want visibility into processes? 👀  
Your toolbox:  
📊 `ps`, `top`, `uptime`, `pstree`  
🖥️ GUI like `gnome-system-monitor`  
And when things misbehave:  
☠️ `kill -15 PID` → polite  
💥 `kill -9 PID` → force  
🔥 `killall` → signal all with same name  
#SysAdmin #Linux

---

**Tweet 3 (Day 3)**  
Foreground & background hacks in Linux:  
✅ `ctrl+c` → kill foreground  
✅ `ctrl+z` → suspend  
✅ `command &` → run in background  
✅ `fg` / `bg` → switch jobs  
✅ `nohup` → detach from shell  
These keep your terminal sessions flexible ⚡  
#LinuxTips

---

**Tweet 4 (Day 4)**  
Scheduling made simple:  
⏱️ `sleep` → quick delays  
📅 `at` → one-time jobs  
🔁 `cron` → recurring tasks via `crontab`

Bonus: Watch **load average**!  
👉 1.0 = 1 fully used CPU core  
👉 Divide by #cores = real system load  
#Linux #DevOps