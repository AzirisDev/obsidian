IF
```
x = input('x = ')
y = input('y = ')

if x < y:
	print('x is less than y')
elif x > y:
	print('y is less than x')
else:
	print('x is equal to y')
	
if 3 < x < 5: // way of writing
	print('x is 4')
```

We have options like `or, and`.

MATCH
```
name = input('Who?')

match name:
	case 'Harry' | 'Ron':
		print("Griff")
	case 'Draco':
		print("Slith")
	case _:
		print("who?" )
```

Links:

202510281138

