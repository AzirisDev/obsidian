I will put here basic stuff that are connected to python.

String manipulation:
```
  name = input('What is your name?')
  name = name.strip() // remove spaces 
  name = name.capitalize() // capitalize first letter in string
  name = name.title() // capitalize each letter
  first, second = name.split(' ')
  print(f'Hello, {name}')
  ```

Integer manipulation - whole numbers
```
x = input('x=')
y = input('y=')

z = int(x) + int(y)
print(z)
```

Float manipulation - number with decimal points
```
x = input('x=')
y = input('y=')

z = float(x) + float(y)
z = round(z, 2) // rounded up the nearest integer
print(f{z:,}) // print like 1,000,000
print(f{z:2f}) // print with 2 decimal number
```

Functions
```
def main():
	name = input("What is your name?")
	hello()
	
def hello(to = 'world'): // default value, used if nothing passed
	print('hello,', to)
	
main() // start the main function, without it file code will contain only function definition
```

Return values in function
```
def main():
	x = input('What is x?')
	print('x squared is', square(x))
	
def square(n):
	return n * n
	
def squareV2(n):
	return pow(n, 2)
	
main()
```
Links:

202510272104

