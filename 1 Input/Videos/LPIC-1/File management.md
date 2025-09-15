### Wildcards
- * - any string
- ? - one character
- [ABC] - matches A or B or C
- [0-9a-z] - all digits and characters
- [!x] - not x

### Commands
- ls -ltrh - long format to see all info in list of files
- cp file1 destination_file - copy content to another file
	- -r - copy everything in it
- mv file destination - moves the files
	- also used for renaming -> mv previous new
- rm - delete files
	- -r - delete everything in directory
- mkdir - create directory
	- -p - create parents if needed
- rmdir - deletes directory
- touch - creates files and change timestamp of a file
- file - determine file type
- find `where` `options`  - find files
	- find / -type d - find all directories, l - links, f - files
	- find / -iname "103" - find files that contains 103 in name
	- -size - filter by size
	- -amin -60 - files that has been accessed in last hour
	- -mmin -60 - files that has been modified in last hour
	- -cmin -60 - files that has been status changed in last hour
	- find / -mmin -60 -exec rm '{}' \; - remove all that filtered files
	- -delete - switch for delete found files

### Compression and Archiving files

Compression - zip one file
Archive - many files in one file
- gzip/guzip filename - zip or unzip file
	- bzip2, xz - other types of zippers
- tar cf file names - creates an archive
	- tar xf archive name - extract archive

Links:

202509131222

