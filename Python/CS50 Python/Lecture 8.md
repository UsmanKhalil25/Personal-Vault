#### Tuple
- returning a sequence of values
```Python

def main():
	name,house = get_student()
	print(f"{name} from {house}")

def get_student():
	name = input("Name: ")
	house = input("House: ")
	return name,house

  

if __name__ == "__main__":
	main()
```

- actually we are returning a tuple with is a list of immutable values
- in list we can change the values in by using indexes, whereas the values in a tuple cannot be changed
```Python
def main():
	student =get_student()
	print(f"{student[0]} from {student[1]}")


def get_student():
	name = input("Name: ")
	house = input("House: ")
	return (name,house)
	
if __name__ == "__main__":
	main()
```

```Python
def main():
	student =get_student()
	if student[0] == "Padma":
	student[1] = "Ravenclaw"
	print(f"{student[0]} from {student[1]}")

  

def get_student():
	name = input("Name: ")
	house = input("House: ")
	return (name,house)

if __name__ == "__main__":
	main()
```

- the tuple is immutable, is the user enter "Padma" as name he will get an TypeError:tuple object does not support value assignment

```Python

def main():
	student =get_student()
	print(f"{student['name']} from {student['house']}")

def get_student():
	student = {}
	student["name"] = input("Name: ")
	student["house"] = input("House: ")
	return student

  

if __name__ == "__main__":
	main()
```
- we have used a dictionary in the above code 

```Python
class Student:

	...
def main():
	student =get_student()
	print(f"{student.name} from {student.house}")


def get_student():
	student = Student()
	student.name = input("Name: ")
	student.house= input("House: ")
	return student

if __name__ == "__main__":
	main()
```

#### instance methods
- when a function is inside a class it is called a method
- it is better to do the error checking inside the methods of class
- ****__init__ method**** in Python is used to initialize objects of a class. It is also called a constructor.
```Python
class Student:
	def __init__(self,name,house):
		self.name= name
		self.house = house

def main():
	student =get_student()
	print(f"{student.name} from {student.house}")

def get_student():
	name = input("Name: ")
	house = input("House: ")
	student = Student(name,house)
	return student

if __name__ == "__main__":
	main()
```

- here self means the object that is being created

```Python
class Student:

def __init__(self,name,house):
	if not name:
		raise ValueError("Missing name")
	if house not in ["Gryffindor","Hufflepuff","Ravenclaw","Slytherin"]:
		raise ValueError("Invalid house")
		self.name= name
		self.house = house
	def __str__(self):
		return f"{self.name} from {self.house}"

  

def main():
	student =get_student()
	print(student)
  

def get_student():
	name = input("Name: ")
	house = input("House: ")
	return Student(name,house)

if __name__ == "__main__":
	main()
```

```python
class Student:

def __init__(self,name,house,patronus):

if not name:

raise ValueError("Missing name")

if house not in ["Gryffindor","Hufflepuff","Ravenclaw","Slytherin"]:

raise ValueError("Invalid house")

self.name= name

self.house = house

self.patronus = patronus

def __str__(self):

return f"{self.name} from {self.house}"

def charm(self):

match self.patronus:

case "Stag":

return "stag emoji"

case "Otter":

return "otter emoji"

case "Jack Russell terrier":

return "jack russell terrier emoji"

case _:

return "no emoji"

  

def main():

student =get_student()

print("Expecto patronum: ")

print(student.charm())

  

def get_student():

name = input("Name: ")

house = input("House: ")

patronus = input("Patronus: ")

return Student(name,house)

  

if __name__ == "__main__":

main()
```

#### decorators
- decorators are functions which are used to change the behavior of other functions
	- @property is used with getter
	- @name.setter is used with setter 
```Python
class Student:

	def __init__(self,name,house):
		if not name:
			raise ValueError("Missing name")
		self.name= name
		self.house = house
		
	def __str__(self):
		return f"{self.name} from {self.house}"
	# Getter
	@property
	def house(self):
		return self._house
	# Setter
	@house.setter
	def house(self,house):
		if house not in ["Gryffindor","Hufflepuff","Ravenclaw","Slytherin"]:
			raise ValueError("Invalid house")
		self._house = house
def main():
	student =get_student()
	print(f"{student.name} from {student.house}")

def get_student():
	name = input("Name: ")
	house = input("House: ")
	return Student(name,house)

if __name__ == "__main__":
	main()
```

- Note that the name of getter and setter is same as the house attribute in our student.house so a naming conflict may occur when assigning or retrieving the values in getter and setter respectively
- therefore we have used self._house to make it clear that we are infact changing the attribute itself
- the setter will automatically be called when we write self.house = house or if we use student.house = something, in both cases the setter will be called
- no that we are not using _  in self.house = house in the __init__ method because we want to call the setter there, whereas if we had used _ in __init__ then the setter would not have been called
- Note that we should only used _ inside the getter and setter 
- if we want to change the value without calling the setter we will write with the underscore because the instance variable or the attribute house is now directly accessed using student._house

#### int,str,list,dict,tuple are also classes

```Python
print(type(50))
print(type("string"))
print(type(list()))
print(type([]))
print(type(dict()))
print(type({}))
print(type(tuple()))
print(type(()))
```

```Python
import random

class Hat:
	houses = ["Gryffindor","Hufflepuff","Ravenclaw","Slytherin"]
	def sort(self,name):
		house = random.choice(self.houses)
		print(f"{name} is in some {house}")

  
def main():
	hat =Hat()
	hat.sort("Harry")

if __name__ == "__main__":
	main()
```


```Python
import random  
  
  
class Hat:  
    houses = ["Gryffindor", "Slytherin", "Hufflepuff", "Ravenclaw"]  
  
    @classmethod  
    def sort(cls, name):  
        print(f"{name} is in {random.choice(cls.houses)}")  
  
  
def main():  
    name = input("Name: ")  
    Hat.sort(name)  
  
  
if __name__ == "__main__":  
    main()
```

- Now we dont need to first create an object of class and then use the methods for it but we can used the classmethods without any class object

```python
class Student:  
    def __init__(self, name, house):  
        self.name = name  
        self.house = house  
  
    def __str__(self):  
        return f"{self.name} from {self.house}"  
    # Getter  
    @property  
    def name(self):  
        return self._name  
      
    # Setter  
    @name.setter  
    def name(self, name):  
        if not name:  
            raise ValueError("Missing name")  
        self._name = name  
  
    # Getter  
    @property  
    def house(self):  
        return self._house  
  
    # Setter  
    @house.setter  
    def house(self, house):  
        if house not in ["Gryffindor","Hufflepuff","Ravenclaw","Slytherin"]:  
            raise ValueError("Invalid house")  
        self._house = house  
  
    @classmethod  
    def get(cls):  
        name = input("Name: ")  
        house = input("House: ")  
        return cls(name,house)  
  
  
def main():  
    student = Student.get()  
    print(f"{student.name} from {student.house}")  
  
  
if __name__ == "__main__":  
    main()
```


```python
class Vault:  
    def __init__(self, galleons=0, sickles=0, knuts=0):  
        self.galleons = galleons  
        self.sickles = sickles  
        self.knuts = knuts  
  
    def __str__(self):  
        return f"{self.galleons} Galleons,{self.sickles} Sickles,{self.knuts} Knuts"  
    def __add__(self, other):  
        galleons = self.galleons + other.galleons  
        sickles = self.sickles + other.sickles  
        knuts = self.knuts + other.knuts  
        return Vault(galleons, sickles, knuts)  
  
  
potter = Vault(100, 50, 25)  
print(potter)  
weasley = Vault(25, 50, 100)  
print(weasley)  
total = potter + weasley  
print(total)
```

- Operator overloading in python
