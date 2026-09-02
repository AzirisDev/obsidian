### For loop structure
```
for VARIABLE in LIST; do
    # Commands using $VARIABLE
done
```

### Number ranges
```
for i in {1..5}; do
    echo "Count: $i"
done

# With step
for i in {0..10..2}; do
    echo "Even: $i"
done
```

### Rule
- always use `*` instead of `ls` or other commands
  
### While loop
```
count=1
while [[ $count -le 5 ]]; do
    echo "Count: $count"
    ((count++))
done
```

### Read file by line
Read file lines ignoring the backslashes:
```
while read -r line; do
    echo "Line: $line"
done < /etc/hosts
```
Read file with specific separator:
```
# /etc/passwd format: user:x:uid:gid:info:home:shell
while IFS=: read -r user _ uid gid _ home shell; do
    echo "$user (UID $uid) uses $shell"
done < /etc/passwd
```

- Use `break` to break the loop
- Use `continue` to skip current step in loop and continue

Links:

202608290134

