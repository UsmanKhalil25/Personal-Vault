```Python
name = input("What's your name? ")
file = open("names.txt","w")

file.write(name)

file.close()
	```

- open() takes two arguments, name of file and the mode in which we want to open the file in
- If the file does not exist, then it creates the files for us
```Python
name = input("What's your name? ")

  

file = open("names.txt","a")

file.write(f"{name}\n")

file.close()
```
- to append names to the next line

```Python
name = input("What's your name? ")


with open("names.txt","a") as file:
	file.write(f"{name}\n")
```
- the above syntax automatically closes the file after writing 

```Python
with open("names.txt","r") as file:
	lines = file.readlines()
for line in lines:
	print(line,end="")
```
- reading all the lines and storing into a list named as lines

```Python
with open("names.txt","r") as file:
	for line in file:
		print(line.rstrip())
```
- rstrip() is used to remove any trailing whitespace at the end of the lines

``` Python
names = []

with open("names.txt","r") as file:
	for line in file:
		names.append(line.rstrip())

  

for name in sorted(names):
	print(name)
```

```Python
with open("names.txt","r") as file:
	for line in sorted(file,reverse=True):
		print(line.rstrip())
```
- The above code sorts the file in reverse order


#### CSV files(comma-separated values)
- Data is written as studentName,studentCity
```Python
with open("students.csv","r") as file:
	for line in file:
		row = line.rstrip().split(",")
		print(f"{row[0]} is in {row[1]}")
```
- row is a list of size 2 

```Python
students =[]

with open("students.csv","r") as file:
	for line in file:
		name,city = line.rstrip().split(",")
		students.append(f"{name} is in {city}")

  

for student in sorted(students):
	print(student)
```


```Python
students =[]

with open("students.csv","r") as file:
	for line in file:
		name,city = line.rstrip().split(",")
		student = {}
		student["name"] = name
		student["city"] = city
		students.append(student)

def get_city(student):
	return student["city"]

  

for student in sorted(students,key = get_city):
	print(f"{student['name']} is in {student['city']}")
```

- In the above code, the get_city function is passed by name to the sorted function
- The sorted function calls the get_city on its own using a student from the students list and uses that key to sort the list.


```Python
students = []
with open("students.csv","r") as file:
	for line in file:
		name,city = line.rstrip().split(",")
		student = {"name":name, "city":city}
		students.append(student)

  

for student in sorted(students,key = lambda student: student["name"]):
	print(f"{student["name"]} is in {student["city"]}")
```

### Lambda Functions in python
- Lambda functions are anonymous i.e they name no name
- Lambda functions are used for functions where one line returns are used
- in syntax
```python
key = lambda student: student["name"]
```
	- the first student is the parameter passed to the function and the student["name"] is the return value

- Lambda functions can take multiple parameters consider the following example

```Python
x = 12
y = 23
z = lambda x, y: x + y
print(z(x, y))
```
- Note that in the third line we are assigning z a lambda function that take two arguments and return their sum

#### CSV in Python
```Python
import csv

  

students = []

  

with open("students.csv","r") as file:
	reader = csv.reader(file)
	for name,city in reader:
		students.append({"name":name,"city":city})

for student in sorted(students,key = lambda student: student["name"]):
	print(f"{student["name"]} is in {student["city"]}")
```
- Suppose that the csv file contains the data in the following form
	- Usman,"Ali Town, Lahore"
	- Abdullah,Dinga
	- Babar,Dubai
- The csv.reader will be able to read "Ali Town, Lahore" as one address.


#### csv. writer
```Python
import csv
name= input("What's your name? ")
address = input("What's your address? ")
with open("students.csv","a") as file:
	writer = csv.writer(file)
	writer.writerow([name,address])
```

#### csv.DictWriter
```Python
import csv
name= input("What's your name? ")
address = input("What's your address? ")
with open("students.csv","a") as file:
	writer = csv.DictWriter(file,fieldnames=["name","address"])
	writer.writerow({"name":name,"address":address})
```


```Python
import sys
from PIL import Image

images = []

for arg in sys.argv[1:]:
	image =Image.open(arg)
	images.append(image)

  

image[0].save(

	"costume.gif",save_all =True,append_images =images[1],duration = 200,loop =0
)

```
- The above code is used to combine two images to create a gif