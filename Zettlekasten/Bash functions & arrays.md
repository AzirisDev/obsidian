### Functions

Function is as in any programming language. Several BUTs
- BUT we can not return from function -> use `echo` and capture it using `$(...)`
- BUT each variable in it by default is global -> use `local` key word to make variable local
Examples of functions:
```
show_info() {
    echo "First arg: $1"
    echo "All args: $@"
    echo "Number of args: $#"
}

show_info one two three
```

```
is_even() {
    local num="$1"
    (( num % 2 == 0 ))
}

if is_even 4; then
    echo "4 is even"
fi
```

```
get_extension() {
    local filename="$1"
    echo "${filename##*.}"
}

ext=$(get_extension "document.txt")
echo "$ext"
```


### Arrays

```
fruits=("apple" "banana" "orange")

# Single element (zero-indexed)
echo "${fruits[0]}"
# apple

# All elements
echo "${fruits[@]}"
# apple banana orange

# Length
echo "${#fruits[@]}"
# 3

# Add element
fruits+=("grape")
```

Arrays stores list of values. 
Links:

202608290204

