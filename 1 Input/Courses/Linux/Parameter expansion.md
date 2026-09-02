We have following commands:
```
# sed - search and replace
echo "hello" | sed 's/hello/hi/'

# awk - extract fields
echo "one two three" | awk '{print $2}'

# tr - translate characters
echo "hello" | tr 'a-z' 'A-Z'

# cut - extract columns
echo "a:b:c" | cut -d: -f2
```

But they can be AND should be replaced by parameter expansion in scripts.
#### Default values
```
#!/bin/bash
name="${1:-world}"
log_level="${LOG_LEVEL:-info}"
echo "Hello, $name (log: $log_level)"
```
- `${var:-default}` - Use default if empty/unset (don’t change var)
- `${var:=default}` - Set default if empty/unset (changes var)
- `${var:?error}` - Error if empty/unset
  
#### String length
```
password="secretpass"
echo "Length: ${#password}"
```

#### Removing patterns
##### Suffix
```
filename="document.txt"
echo "${filename%.txt}"
# document

filepath="backup.2024.tar.gz"
echo "${filepath%.*}"
# backup.2024.tar (shortest match)
echo "${filepath%%.*}"
# backup (longest match)
```
##### Prefix
```
filepath="/home/user/document.txt"
echo "${filepath#*/}"
# home/user/document.txt (shortest match)
echo "${filepath##*/}"
# document.txt (longest match - this is basename!)
```


### Search and replacement
```
text="hello world world"

# Replace first match
echo "${text/world/bash}"
# hello bash world

# Replace all matches
echo "${text//world/bash}"
# hello bash bash

# Delete (replace with nothing)
echo "${text// /}"
# helloworldworld
```


### Case transformation
```
name="hello world"
echo "${name^}"
# Hello world (capitalize first)
echo "${name^^}"
# HELLO WORLD (uppercase all)

name="HELLO WORLD"
echo "${name,,}"
# hello world (lowercase all)
```



Links:

202608281829

