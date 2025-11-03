`tuple` - collection of values, immutable - we can not change the values.
`return value1, value2` - returning tuple.

`Classes` - to invent the data types; blueprint for the object
`Object` - instance of class.

```
class Student:
	def __init__(self, name, house):
		if not name:
			raise ValueError("Missing name")
		self.name = name
		self.house = house
		
	def __str__(self):
		return f"{self.name} from{self.house}"
	
	@property  // Getter
	def name(self):
		return self._name
		
	@name.setter  // Setter
	def house(self, name):
		// We can put there some checker etc
		// To prevent assign values directly
		self._name_ = name
		
	@property  // Getter
	def house(self):
		return self._house
		
	@house.setter  // Setter
	def house(self, house):
		// We can put there some checker etc
		// To prevent assign values directly
		self._house = house

def main():
	student = get_student()
	print(student)
	
def get_student():
	student = Student()
	student.name = input("Name: ")
	student.house = input("House: ")
	return student
	
if __name__ == "__main__":
	main()
```


We can create alike static methods inside class.
We also have @staticmethod - need to dig deep in.

```
class Hat:
	@classmethod
	def example(cls, test1):
		print(test1, cls.names)
		

Hat.example("hhahah") // we do not need instance of a class to use function
```

#### Inheritance
```
class Wizard:
	def __init__(self, name):
		self.name = name
	
class Student(Wizard):
	def __init__(self, name, house):
		super().__init__(name) = name
		self.house = house
```

#### Operator overloading
interaction between classes
```
def __add__(self, other):
	x = self.x + other.x
	y = self.y + other.y
	return Cls(x, y)
```

Links:

202511031648

