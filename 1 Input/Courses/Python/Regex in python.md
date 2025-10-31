Search in internet or in libraries: there are plenty of them.
```
email = input('What is your email?').strip()

if '@' in email and '.' in email:
	print('valid)
```
It is all buggy. We can use `re` library to work with regex.

```
import re

email = input('What is your email?').strip()

if re.search(r"^\w+@(\w+\.)?\w+\.(edu|com|net)$", email, re.IGNORECASE): 
// azim@nu.edu; r for raw string
// \w = [a-zA-Z0-9_] - for word
	print('valid')
```

`re.sub(pattern, to_what, string)` - replace subgroup in string

Regex symbols:
- `.` - any character expect newline
- `*` - 0 or more repetitions
- `+` - 1 or more repetitions
- `?` - 0 or 1 repetition
- `{m}` - m repetitions
- `{m,n}` - m to n range repetitions
- `^` - start of the string
- `$` - end of the string. 
- `[]` - set characters
- `[^]` - can not match these characters
- `\d` - decimal
- `\D` - not a decimal
- `\s` - whitespace characters
- `\S` - no whitespace 
- `\w` - word
- `\W` - not a word
- `A|B`
- `(...)` - combine ideas


Links:

202510311313

