#### while loop
```python
i = 0

while i < 3:
	print("meow")
	i = i+1
```
#### for loop
- Note: The for loop is used to iterate through a list of items 
```Python
for i in [0,1,2]:
	print("meow")
```

```python
for i in range(3):
	print("meow")
	print(i)
```
- the above code execute for i  = 0,1,2 
- Note that in the above code we are not using i in any useful way
```Python
for _ in range(3):
	print("meow")
```

```Python
def get_number():

while True:

number = int(input("Enter number: "))

if number >0:

return number

  

def meow(n = 0):

for _ in range(n):

print("meow")

def main():

number = get_number()

meow(number)

  

main()
```

```Python
students = ["Hermoine","Harry","Ron"]

  

for student in students:
	print(student)
```
#### Another way to use lists
```Python
students = ["Hermoine","Harry","Ron"]
for student in students:
	print(student)
for i in range(len(students)):
	print(students[i])
```

#### Dictionary in Python
-  Key-Value pairs
```Python
students = {"Hermoine":"Gryffindor","Harry":"Gryffindor","Ron":"Gryffindor","Draco":"Slytherin"}

print(students["Hermoine"])
print(students["Draco"])
```

- the following code will give us only the keys of the dictionary
```Python
students = {"Hermoine":"Gryffindor","Harry":"Gryffindor","Ron":"Gryffindor","Draco":"Slytherin"}
for students in students:
	print(students)
```

#### List of dictionaries
```Python
students = [

{"name":"Hermoine","house":"Gryffindor","patronus":"Otter"},

{"name":"Harry","house":"Gryffindor","patronus":"Stag"},

{"name":"Ron","house":"Gryffindor","patronus":"Jack Russel terrier"},

{"name":"Draco","house":"Slytherin","patronus":None}

]

for student in students:
	print(student["name"],student["house"],student["patronus"],sep=" , ")
```