- df -iTh - disk free spaces among whole system, etc, human readable, types of file system, inodes count
	- inodes - data structure to track the created files (ext file system has limited inodes)
- du -h `path`- disk usage of directory
	- watch du - real time monitor of disk usage command
	- --max-depth 1 - first level summary

- fsck - file system check for errors and optionally fix them -> identifies the file system types and run necessary command from `/sbin/`
	- -N show errors without making changes

**Key XFS Commands**
- **xfs_repair**: The main tool for checking and repairing a damaged XFS filesystem. It's the equivalent of `fsck` for XFS. The `-n` option can be used to check without making any changes.
- **xfs_info**: Displays information about an XFS filesystem.
- **xfs_db**: A debugging tool used to examine and debug an XFS filesystem

Links:

202509161754

