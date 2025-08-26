- ssh username@hostname - login remotely
- exit - to logout
- 
- shutdown -h 10:00 "message" - shutdown system at 10 o'clock by notifying other users
- shutdown -r - reboot the system
- shutdown -c - cancel shutdown
- 
- cd - -return back from directory
- pwd - print working directory
- 
- tree - display directories in tree manner; -d for directories; you can add directory path for certain tree
- 
- Hard links - creating different names for the same file; good for backup
	- ln file1.txt file2.txt
- Symlinks - one file stores pointer to another one; for shortcuts, organizing
	- ln -s file1.txt file2.txt
- 
- mv - rename file/directory
- rm/rmdir - remove file, directory
- 
- [[Standard File Streams]]
- [[Pipes]]
- 
- locate 'string' - find file name contains "string"; it is fast and rely on presaved file system database; only search for names, not content
	- sudo updatedb - updates the database of files in system
- wildcards - replacors of characters
	- a* - starts from "a"
	- a\*log\* - starts from "a" and containes after "log"
	- a[p-z]* - starts with a, and continued by any character in p-z range
	- ? - replaces only one character
- find - powerful tool to search by name, created time, type, size, permission
	- find "place" "option" "argument"
	- 

Links:

202508241239

