 Modules - libraries - file that have already written code for reusability.
`random` library provides functions to work with random numbers.

```
import random

x = random.choice(1..4)
print(x)
y = random.randint(1,9)
print(y)

list = [1,2,3,4]
random.shuffle(list)
print(list)
```

```
from random import choice

x = choice(1..4)
print(x)
```

```
import statistics

statistics.mean([1,2,3,4])
```

`sys.argv` - gives what we put into terminal before running it

if I run - `python name.py Azim` or `python name.py "Azim Sattykov"`
I will have - `My name is Azim` or `My name is Azim Sattykov`

- `sys.argv[0]` - name of the file aka name.py
```
import sys

print("My name is", sys.argv[1])
sys.exit("Error) // exits the program

for arg in sys.argv[1:]: // slice, start at 1 index
	print(arg)
	
for arg in sys.argv[:-1]: // slice, start at 1 index from the end
	print(arg)
```

#### Packages
Module implemented in a folder - 3rd party library and gain access to more functionality.
`pip` - program that allows to install python packages

#### APIs
Application Programming Interfaces - 3rd services with set of distinct functions.
`pip install requests`

```
import requests
import json
import sys

if len(sys.argv) != 2:
	sys.exit()
	
response = requests.get("https://google.com" + sys.argv[1])
print(json.dumps(response.json(), indent = 2))
```
 
Links:

202510291427

