#### Set
Collection of values without duplicates.
```
example = set()
example.add(val)
```

#### Global vars
```
balance = 0

def withdraw(n):
	global balance
	balance -= n
```

#### Constants
```
MEOWS = 3

for _ in range(MEOWS):
	print("meow")
```

#### Docstrings - standard way of documenting
```
def example(n) -> str:
	```
	Meow n times
	
	:param n: number of times moew
	:type n: int
	:raise TypeError: if n is not int
	:return: A string of meows
	:rtype: str
	```
	return "meow" * n
```

#### Arguments work with argparse
```
import argparse

parser = argparse.ArgumentParser(description="Meow like a cat")
parser.add_argument("-n", default=1, help="Number of meows", type=int)
args = parser.parse_args()

for _ in range(args.n):
	print("meow")
```


Links:

202511041355

