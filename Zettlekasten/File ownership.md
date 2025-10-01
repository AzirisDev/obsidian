Every file in Linux has its owner as user and group.
We have here permission like read(r), write(w), execute(x).
We also have s - setuid -> runs the file with owner's permissions, not the runners.
We have t - sticky bit -> appears in others execution sections; it blocks others from deleting/modifying your files.
Permissions affect users, groups, others.

Example:
d-rwx-wx-x -
- file is directory
- user - can read, write and execute
- group - can write and execute
- others - can execute

### Change file permissions
- chmod uo+x, g-w filename - users and others now can execute, group can not write in file
- chmod 755 filename  (7 - users, 5 - group, 5 - others)
	- 1 = execute, write = 2, read = 4
	- 7 - read, write, execute
	- 6 - read, write
	- 5 - read, execute
	- 4 - read
	- 3 - write, execute
	- 2 - write
	- 1 - execute
	- 0 - none

### Change ownership of file
- sudo chown new_owner filename
- sudo chgrp new_group filename

#### Umask
- umask - shows default permissions for files
	- 666 - umask = default permission
	- Example: umask = 002 -> 666 - 002 = 664 -> that is default permission set for file system

Links:

202508290035

