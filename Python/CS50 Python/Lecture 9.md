```Python
students = [

{"name":"Hermoine","house":"Gryffindor"},

{"name":"Harry","house":"Gryffindor"},

{"name":"Ron","house":"Gryffindor"},

{"name":"Draco","house":"Slytherin"},

{"name":"Padma","house":"Ravenclaw"}

]

  

houses = []

  

for student in students:

if student["house"] not in houses:

houses.append(student["house"])

  

for house in sorted(houses):

print(house)
```

- in the above code we are extracting the names of houses from the students dictionary and printing them in sorted order
#### Set
```Python
students = [

{"name":"Hermoine","house":"Gryffindor"},

{"name":"Harry","house":"Gryffindor"},

{"name":"Ron","house":"Gryffindor"},

{"name":"Draco","house":"Slytherin"},

{"name":"Padma","house":"Ravenclaw"}

]

  

houses = set()

  

for student in students:

houses.add(student["house"])

  

for house in sorted(houses):

print(house)
```

- in the above code we have used set() to place the houses.
#### global variables in python

```Python
balance = 0

  
  

def deposit(amount):
	
	global balance
	
	balance += amount

  
  

def withdraw(amount):

	global balance
	
	balance -= amount

  
  

def main():

	print(f"Balance: {balance}")
	
	deposit(100)
	
	withdraw(50)
	
	print(f"Balance: {balance}")

  
  
  

if __name__ == "__main__":

	main()
```

- we use the global keyword to change the value of balance although we can print the value without telling the function that it is a global variable, when changing it we have to explicitly tell that the variable is global

```Python
class Account:
    def __init__(self):
        self._balance= 0

    @property 
    def balance(self):
        return self._balance
    
    def deposit(self, amount):
        self._balance += amount
    
    def withdraw(self, amount):
        self._balance -= amount

def main():
    account = Account()
    print(f"Balance: {account._balance}")
    account.deposit(100)
    account.withdraw(50)
    print(f"Balance: {account._balance}")

if __name__ == "__main__":
    main()

```

#### constants
- the naming copynvention for constants in python is all capital characters
- python constants are although mutable (can be changed) so technically there are no constants in python
- we can create constants in class though
```Python
class Cat:
    MEOWS = 3

    def meow(self):
        for _ in range(Cat.MEOWS):
            print("meow")

cat = Cat()
cat.meow()
```
- creating constants in python

####  Type- Hinst: type checking using mypy
```Python
def meow(n: int):
    for _ in range(n):
        print("meow")



number: int = int(input("Number: "))
meow(number)

```

- run mypy filename.py first before running the code
- note that we have used :int where we want to tell mypy that this variable or parameter should be int
```Python
def meow(n: int) -> None:
    for _ in range(n):
        print("meow")



number: int = int(input("Number: "))
meows: str = meow(number)
print(meows)

```
- note that we have used -> None to specify that this function returns none, which will help in debugging the error in second last line

```Python
def meow(n: int) -> str:
    return "meow\n"* n


number: int = int(input("Number: "))
meows: str = meow(number)
print(meows,end = "")

```
- this will correct the error found my mypy


#### Docstrings

```Python
def meow(n: int) -> str:
    """meow n times"""
    return "meow\n"* n


number: int = int(input("Number: "))
meows: str = meow(number)
print(meows,end = "")
```
- in python """comment""" is used to document functions or methods 
- this helps in analyzing the code by using another third party software
```Python
def meow(n: int) -> str:
    """
    meow n times

    :param n: number of times to meow
    :type n: int
    :raise TypeError: if n is not an int
    :return: a string of n meows, one per line
    :rtype: str
    """
    if n is not int():
        raise(TypeError)
    
    return "meow\n"* n


number: int = int(input("Number: "))
meows: str = meow(number)
print(meows,end = "")

```

- how to document functions in python

#### arg prase
```Python
import sys

if len(sys.argv) ==1:
    print("meow")
elif len(sys.argv) == 3 and sys.argv[1] == "-n":
    n = int(sys.argv[2])
    for _ in range(n):
        print("meow")
else:
    print("usage: meow.py")

```
- in the above code we are using sys to access the command-line arguments entered by the user
- the argument should be python3 filename.py -n 2
- where -n is indicates that anything entered after that will be the number of times meow is printed on the screen

```Python
import argparse

parser  =argparse.ArgumentParser(description="Meow like a cat")
parser.add_argument("-n", help = "number of times to meow")
args = parser.parse_args()


for _ in range(int(args.n)):
    print("meow")
```
- run python3 meow.py -h to access the help for this python file

```Python
import argparse

parser  =argparse.ArgumentParser(description="Meow like a cat")
parser.add_argument("-n",default= 1, help = "number of times to meow",type=int)
args = parser.parse_args()


for _ in range(int(args.n)):
    print("meow")

```



#### unpacking
```python
def total(galleons, sickles, knuts):
    return (galleons * 17 + sickles) * 29 + knuts

coins = [100, 50, 25]

print(f"{total(coins[0], coins[1], coins[2])} Knuts")
```

- what if we want to pass the coins list 

```Python
def total(galleons, sickles, knuts):
    return (galleons * 17 + sickles) * 29 + knuts

coins = [100, 50, 25]

print(f"{total(*coins)} Knuts")
```

- this * operator which is unpacking the list only works with lists 

```Python
def total(galleons, sickles, knuts):
    return (galleons * 17 + sickles) * 29 + knuts


print(f"{total(galleons=100, sickles=50, knuts=25)} Knuts")

```
- another way of doing the same thing
```Python
def total(galleons, sickles, knuts):
    return (galleons * 17 + sickles) * 29 + knuts

coins = {"galleons":100,"sickles":50,"knuts":25}

print(f"{total(**coins)} Knuts")

```

- when unpacking a dictionary we have to use  **

```Python
def f(*args, **kwargs):
    print("Positional:",args)


f(100,50,25,5)
```

- * args can contain a sequence of arguments 
- ** kwargs can contain a sequence of key word arguments (dictionaries)
```Python
def f(*args, **kwargs):
    print("Named:",kwargs)


f(galleons= 100,sickles=50,knuts=25)
```
- in the above code the kwargs will be a dictionary with key =  name that has passed 
```Python
def f(*args, **kwargs):
    print("Positional:",args)
    print("Named:",kwargs)


f(80,23,galleons= 100,sickles=50,knuts=25)
```
- the position of positional arguments and named arguments matter we cannot swap them

#### map
```Python
def main():
    yell(["This", "is", "CS50"])


def yell(words):
    uppercased = []
    for word in words:
        uppercased.append(word.upper())
    print(*uppercased)

if __name__ == "__main__":
    main()
```

```Python
def main():
    yell("This", "is", "CS50")


def yell(*words):
    uppercased = []
    for word in words:
        uppercased.append(word.upper())
    print(*uppercased)

if __name__ == "__main__":
    main()
```

- another usage of * args and unpacking
```Python
def main():
    yell("This", "is", "CS50")


def yell(*words):
    uppercased = []
    for word in words:
        uppercased.append(word.upper())
    print(*uppercased)

if __name__ == "__main__":
    main()
```

#### list comprehension
```Python
def main():
    yell("This", "is", "CS50")


def yell(*words):
    uppercased = [word.upper() for word in words]
    print(*uppercased)

if __name__ == "__main__":
    main()
```

```Python
students = [
    {"name":"Hermoine","house":"Gryffindor"},
    {"name":"Harry","house":"Gryffindor"},
    {"name":"Ron","house":"Gryffindor"},
    {"name":"Draco","house":"Slytherin"},
    {"name":"Padma","house":"Ravenclaw"}
]

gryffindors = [student["name"] for student in students if student["house"] == "Gryffindor"]

for gryffindor in sorted(gryffindors):
    print(gryffindor)
```


#### filter()
```Python
students = [
    {"name":"Hermoine","house":"Gryffindor"},
    {"name":"Harry","house":"Gryffindor"},
    {"name":"Ron","house":"Gryffindor"},
    {"name":"Draco","house":"Slytherin"},
    {"name":"Padma","house":"Ravenclaw"}
]

def is_gryffindor(student):
    return student["house"] == "Gryffindor"


gryffindors = filter(is_gryffindor,students)

for gryffindor in sorted(gryffindors,key = lambda student:student["name"]):
    print(gryffindor["name"])
```


#### dictionary comprehensions
```Python
students = ["Hermoine","Harry","Ron"]

gryffindors = []

for student in students:
    gryffindors.append({"name":student,"house":"Gryffindor"})

for gryffindor in gryffindors:
    print(gryffindor)
```

```Python
students = ["Hermoine","Harry","Ron"]

gryffindors = [{"name":student,"house":"Gryffindro"} for student in students]

for gryffindor in gryffindors:
    print(gryffindor)
```
- note that we have solved the above problem using list comprehension

```python
students = ["Hermoine","Harry","Ron"]

gryffindors = {student: "Gryffindor" for student in students}

for gryffindor in gryffindors:
    print(gryffindor)
```
- in the above code we have used a dictionary comprehension


#### enumerater

```Python
students = ["Hermoine","Harry","Ron"]

for i in range(len(students)):
    print(i+1,students[i])
    
```

```python
students = ["Hermoine","Harry","Ron"]

for i,student in enumerate(students):
    print(i+1,student)
    
```
- note that now instead of using i to access each student we are just using student

#### generators
```Python
def sheep(n:int):
    flock = []
    for i in range(n):
        flock.append("🐑"*i)
    return flock


def main():
    n: int = int(input("What's n? "))
    for s in sheep(n):
        print(s)


if __name__ == "__main__":
    main()
```
- note that if we enter n = 100000 the program will be killed or crashed
- because we are returning 100000 rows of sheeps that is causing the memory to be filled 
- we want to return one value at a time to not fill up the whole memory
```Python
def sheep(n: int):
    for i in range(n):
        yield "🐑" * i


def main():
    n: int = int(input("What's n? "))
    for s in sheep(n):
        print(s)


if __name__ == "__main__":
    main()

```
