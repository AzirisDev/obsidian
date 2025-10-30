Write to file:
```
name = input('What is your name?')

file = open('names.txt', 'w') // w - for open file to write, recreates file
							  // it wipes out information
							  // a - for append

file.write(name)
file.close()

OR

with open('names.txt', 'a') as file:
	file.write(f'{name}\n') 

```

Read from file:
```
with open('names.txt', 'r') as file: // r - for read from file
	lines = file.readlines()
	OR
	for line in file:
		print('hello,', line. strip()) 
```

We have `sorted()` function with different parameters to sort iterable object.
Example to sort by name:
```
sorted(students, key=get_name)
def get_name(student):
	return student['name']
	
OR

sorted(students, key=lambda student: student['name'])
// here I got unnamed function
```

### CSV library to work easily with files
Read csv file:
```
import csv

students = []

with open('students.csv') as file:
	reader = csv.reader(file)
	for row in reader:
		students.append({'name': row[0], 'home': row[1]})
		
	OR
	
	// but at the beginning of the csv file we should put name of columns on top
	reader = csv.DictReader(file)
	for row in reader:
		students.append({'name': row['name'], 'home': row['home']})
		OR
		students.append(row)
		
// csv helps us to not get into details of files, like what is the separator, etc
```

Write csv file:
file contains headers: `name, home`
```
import csv

name = input('name?')
home = input('home?')

with open('file.csv', 'a') as file:
	writer = csv.writer(file)
	writer.writerow([name, home])
	
	OR
	
	writer = csv.DictWriter(file, filenames=['name', 'home'])
	writer.writerow({'name': name, 'home': home})
```

We can read and write any type of files: text files, binary, audio, video, etc.
Links:

202510301730

