- Test command - `[[]]`
	- `if [[ "$name" == "DevOps" ]]; then` - everything should have space around
	- always use double brackets
- String comparison:
	- ```
		str1="hello"
		str2="world"
		
		[[ "$str1" == "$str2" ]] && echo "Equal"
		[[ "$str1" != "$str2" ]] && echo "Not equal"
		
		# Empty/not empty
		[[ -z "$name" ]] && echo "Empty"
		
		[[ -n "$name" ]] && echo "Not empty"
	```
- Numeric comparison:
	- `$count -eq 5`
	- `-eq`Equal
	- `-ne`Not equal
	- `-gt`Greater than
	- `-lt`Less than
	- `-ge`Greater than or equal
	- `-le`Less than or equal
- Arithmetic:
	- Inside `(( ))`: use `<`, `>`, `==`, no `$` needed for variables.
- File tests:
	- `-f FILE`File exists and is regular file
	- `-d FILE`Directory exists
	- `-e FILE`Exists (file or directory)
	- `-r FILE`Readable
	- `-w FILE`Writable
	- `-x FILE`Executable
	- `-s FILE`Exists and not empty
- if/else statements:
	- ```
		#!/bin/bash
		
		if [[ -f "$1" ]]; then
		    echo "It's a file"
		elif [[ -d "$1" ]]; then
		    echo "It's a directory"
		else
		    echo "Not found: $1"
		fi
	```
- Checking command existence:
	- ```
		if command -v docker &>/dev/null; then
		    echo "Docker is installed"
		else
		    echo "Docker is not installed"
		fi
	```
- Case statements:
	- ```
		case $1 in
		    start)
		        echo "Starting service..."
		        ;;
		    stop)
		        echo "Stopping service..."
		        ;;
		    *)
		        echo "Usage: $0 {start|stop}"
		        exit 1
		        ;;
		esac
	```

Links:

202608290018

