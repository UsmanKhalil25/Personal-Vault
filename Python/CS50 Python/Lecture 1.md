```Python
score = int(input("Score: "))

if score <= 100 and score >=90:

	print("Grade A")

elif score < 90 and score >=80:

	print("Grade B")

elif score < 80 and score >=70:

	print("Grade C")

elif score < 70 and score >=60:

	print("Grade D")

else:

	print("Grade F")
```


- Another way to do this:
```Python
score = int(input("Score: "))

if 90 <= score <= 100:
	print("Grade A")
elif 80 <= score < 90:
	print("Grade B")
elif 70 <= score < 80:
	print("Grade C")
elif 60 <= score < 70:
	print("Grade D")
else:
	print("Grade F")
```
- Or like this
```Python
score = int(input("Score: "))

  

if score >=90:

print("Grade A")

elif score >=80:

print("Grade B")

elif score >=70:

print("Grade C")

elif score >=60:

print("Grade D")

else:

print("Grade F")
```

#### match in python (equivalent of switch in C++)
```Python
name = input("Enter your name: ")

match name:

case "Harry":

print("Gryffindor")

case "Hermione":

print("Gryffindor")

case "Ron":

print("Gryffindor")

case "Draco":

print("Slytherin")

case _:

print("Who?")
```

```Python
name = input("Enter your name: ")


match name:

case "Harry" | "Hermoine" |"Ron":

print("Gryffindor")

case "Draco":

print("Slytherin")

case _:

print("Who?")
```