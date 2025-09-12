#### Viewing commands
- cat - shows the content of file/s
	- zcat or something like that depending on file extension - unzip in RAM and shows the content, without explicitly unzipping the file to the main memory
-  less - shows content of large file in pagination manner
- od - octal dumb, shows content in base8 -> usually used to understand problems with text itself

### Selecting commands
-  split `options` `filename` `prefix of parts` - split file
	- -l 100 - option to split to 100 line
	- -d - option to names parts by numbers
	- -n 3 - option to split only to three parts
- head/tail - first/last lines of file
	- head/tail -10 file - print first/last 10 lines files
	- tail -f filename - to see last lines of growing log files
- cut `options` `filename` - separates each line by delimiter to fields
	- cut -d, -f 2 filename - separate lines by "," and get the second field after comma

### Modifying commands
- nl - add line numbers
- sort - sorts the lines in file
	- -n - by numbers at the start
	- -r - reverse sort
- uniq - sort the file and then omit the repeated stuff
	- -c - number of repeated stuff
	- -u - unique one
- tr - translate/change the "prev" to "new", but after piping commands
- sed - stream editor
	- sed 'script' filename - 's/a/b'

### Getting stats commands
- wc - shows line numbers, words, characters
	- -l - number of lines only
- hashing - function that converts input to "random" output, but never changes if input is the same
	- sha256sum - 256 bits output
	- sha512sum - 512 bits output
	- md5sum - old, not really safe
	- security - save not password, but hash of it -> recalculate the input from hash is very time consuming 
Links:

202509121249

