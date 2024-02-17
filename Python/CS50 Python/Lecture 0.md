```python
name = input("Enter your name: ")
print("Hello,",name)
```
- We will get a space between Hello and the name entered by the user due to the parameters that are passed in the print function

- The print function puts a space if more then one parameters are passed to the function
```python
name = input("Enter your name: ")
print("Hello,")
print(name)
```
- Hello and name will appears on two lines
- The print functions prints a \n by default which puts the text of next print instruction on the next line
#### end = "\n"
- How to prevent the above behavior
```python
name = input("Enter your name: ")
print("Hello,", end="")
print(name)
```

#### sep = " "
```python
name = input("Enter your name: ")
print("Hello,",name ,sep="-")
```

#### Use of " " and ' '
```Python
print('Hello, "friend"')
print("Hello ,'friend'")
```
- Using \" 
```Python
print("Hello, \"friend\"")
```
- The same can be used for \'
#### Formatting str
```Python
name = input("Enter your name: ")
print(f"Hello, {name}")
```

#### str.strip()
```Python
name =input("Enter your name: ")
name = name.strip()
print(f"Hello,{name}")
```
- Using some more str funcitons 
	- capitalize ->  capitalize the first word
	- title -> capitalize each word
```Python
name =input("Enter your name: ")
name = name.strip()
name =name.capitalize()
name = name.title()
print(f"Hello,{name}")
```

```Python
name = input("Enter your name: ")
name =name.strip().title()
print(f"Hello, {name}")
```


```Python
name = input("Enter your name: ").strip().title()
print(f"Hello, {name}")
```

#### str.split(ch)
```Python
name = input("Enter your name: ").strip().title()

firstName ,secondName = name.split(" ")

print(f"Hello, {firstName}")
```
- The above code will split the string when it finds the char passed as argument, which in this case is " ", and assign the first part of the string to firstName and the second part to secondName 
```Python
num1 = input("Enter the first number: ")

num2 = input("Enter the second number: ")

result = num1+ num2

print(f"Sum: {result}")
```
- In the above case the + operator will concatenate the inputs from the user, which will be str in this case and not int by default
```Python
num1 = input("Enter the first number: ")

num2 = input("Enter the second number: ")

result = int(num1)+ int(num2)

print(f"Sum: {result}")
```

#### More on formatting str
```python
num1 = float(input("Enter fisrt number: "))

num2 =float(input("Enter second number: "))

sum = int(num1+num2)

print(f"Sum: {sum:,}")
```
- This is used to add a comma such as 1,000 in answers
```Python
num1 = float(input("Enter fisrt number: "))

num2 = float(input("Enter second number: "))

result = round(num1/num2,2)

print(f"Result: {result}")
```
- If we divide num1 = 2 by num2 =3 we will get 0.66666.... , but by using round without the second argument, which is 2 in this case, we will get 1 which is the nearest int to 0.66666...., By using the second argument, we specify the number of digits after the decimal point. For example in this case we will get 0.67

#### Functions in Python
```Python
def hello(name= "User"):
	name =name.title().strip()
	print(f"Hello, {name}")
hello()
name =input("Enter your name: ")
hello(name)
```

```Python
def main():
	num = int(input("Enter number: "))
	
	print(f"Square of {num} is: {square(num)}")

  
  

def square(number):

	return number * number

  

main()
```

```Python
def square(number):

return number ** 2
```
- Or we can use pow() just like in C++