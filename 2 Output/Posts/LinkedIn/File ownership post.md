⚙️ File ownership in Linux is like the **invisible social contract** of your system.

Every file knows _who owns it_, _who can touch it_, and _who better stay away._

Here’s how the whole system of trust works 👇

✅ **Every file has an owner and a group**  
Permissions are split between:
1. **User** — the owner.
2. **Group** — collaborators.
3. **Others** — everyone else.

Each can have:
- `r` = read,
- `w` = write,
- `x` = execute.

✅ **Special permissions**
- `s` (setuid) — lets a file run with the _owner’s_ permissions, not the runner’s.
- `t` (sticky bit) — prevents others from deleting or modifying your files in shared directories.

✅ **Changing permissions and ownership**
- `chmod uo+x, g-w file` — add execute for user and others, remove write for group.
- `chmod 755 file` — full access for owner, read and execute for others.
- `chown new_owner file` — change owner.
- `chgrp new_group file` — change group.

✅ **Default permissions — the umask rule**  
Your system uses `umask` to define what’s allowed by default.  
Example:  
If `umask = 002`, and default file permission is `666`, the result is `664` — meaning owner and group can write, others can’t.

Once you understand this, Linux stops being restrictive. It becomes a system of clear boundaries and trust — one that you control fully.

How do you usually set default permissions for your projects or shared folders? 👇

#Linux #DevOps #SysAdmin #Permissions #CloudNative
![[Gemini_Generated_Image_be1a11be1a11be1a.png]]