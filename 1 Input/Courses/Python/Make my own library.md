`sayings.py` - my module

```
def main():
	hello('world')

def hello(to):
	print('Hello', to)
	
if __name__ == "__main__":
	main()
```

other file:
```
import sys
from sayings.py import hello

if len(sys.argv) == 2:
	hello(sys.argv[1])
```

Links:

202510291507

