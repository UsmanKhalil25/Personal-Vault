#### try and except
- ValueError
```Python
try:

	number = int(input("Enter number: "))

	print(f"Number: {number}")

except ValueError:

	print("number is not an integer")
```
	- If we enter cat in the input which is taking int() we will get valueError

- NameError
```Python
try:

	x = int(input("What's x? "))

except ValueError:

	print("x is not an integer")


print(f"x: {x}")
```
	-In this case we will get NameError, the except statement will print x is not an integer but print will try to print x which is not assigned any value in this case successfully
- Correct version
```Python
try:

	x = int(input("What's x? "))

except ValueError:

	print("x is not an integer")

else:

	print(f"x: {x}")
```

```Python
def main():
	x = get_int()
	print(f"x is {x}")

  

def get_int():
	while True:
		try:
			x = int(input("What's x? "))
			return x
		except ValueError:
			print("x is not an integer")



main()
```

#### pass
```Python
def main():
	x = get_int()
	print(f"x is {x}")

  

def get_int():
	while True:
		try:
			x = int(input("What's x? "))
			return x
		except ValueError:
			pass



main()
```
