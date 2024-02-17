## [Libraries](https://cs50.harvard.edu/python/2022/notes/4/#libraries)

- Generally, libraries are bits of code written by you or others can you can use in your program.
- Python allows you to share functions or features with others as “modules”.
- If you copy and paste code from an old project, chances are you can create such a module or library that you could bring into your new project.


```Python
import random
coin = random.choice(["heads","tails"])
print(coin)
```
	Note: In the above code we are importing the whole random library
	
```python
from random import choice

coin = choice(["heads","tails"])
print(coin)
```
	Note: Now we are only importing the choice function from random library

```Python
import random

number =random.randint(0,9)
print(number)
```

```Python
import random

cards =["jack","queen","king"]
random.shuffle(cards)

print(cards)
```
	Note: random.shuffle returns none but it change the original list passed as argument

#### Command-line-arguments
```Python
import sys
print("hello, my name is", sys.argv[1])
```
- sys.argv means vector of arguments 
- When we run the python file on terminal by
	```python3 main.py Usman ```
	we  are acutally giving the arguments to argv
- Note that we are printing argv[1] which will contains the name argv[0] contains the filename
```Python
import sys

try:
	print("Hello, my name is",sys.argv[1])
except IndexError:
	print("Too few arguments")
```
	Note: trying to handle indexError that can be raised from this code

```Python
import sys
if len(sys.argv)>2:
	sys.exit("Too many arguments")
elif len(sys.argv)<2:
	sys.exit("Too few arguments")

print("Hello, my name is",sys.argv[1])
```

```Python
import sys
if len(sys.argv)<2:
	sys.exit("Too few arguments")
for arg in sys.argv[1:]:
	print("Hello, my name is",arg)
```
- The above code supports multiple arguments 
- We are using slice [1:] which means that start from the first index till the last 
## [Packages](https://cs50.harvard.edu/python/2022/notes/4/#packages)

- One of the reasons Python is so popular is that there are numerous powerful third-party libraries that add functionality. We call these third-party libraries, implemented as a folder, “packages”.
- PyPI is a repository or directory of all available third-party packages currently available.


# Difference in Modules, Library and Packages
In Python, libraries, modules, and packages are all ways to organize and structure code for better manageability, reusability, and maintainability. Let's clarify the differences between them:

1. **Module:**
   - A module is a single Python file that contains Python code.
   - It can define functions, classes, and variables, and it can also include executable code.
   - Modules help in organizing code logically and provide a way to reuse code across different parts of a program.

   Example: If you have a file named `my_module.py`, it can be considered a module, and you can use its functions and variables in other Python scripts.

   ```python
   # my_module.py
   def greet(name):
       print(f"Hello, {name}!")
   ```

   ```python
   # another_script.py
   import my_module

   my_module.greet("John")
   ```

2. **Package:**
   - A package is a collection of Python modules organized in a directory hierarchy.
   - It includes a special `__init__.py` file (which can be empty) to indicate that the directory should be treated as a package.
   - Packages help in organizing related modules into a single directory and prevent naming conflicts.

   Example: If you have a directory named `my_package` with `__init__.py` and `module1.py` inside it, it can be considered a package.

   ```
   my_package/
   ├── __init__.py
   ├── module1.py
   ```

   ```python
   # module1.py
   def add_numbers(a, b):
       return a + b
   ```

   ```python
   # another_script.py
   from my_package import module1

   result = module1.add_numbers(2, 3)
   ```

3. **Library:**
   - A library is a collection of modules or packages.
   - It's a set of pre-written code that can be reused for common tasks.
   - Python has a standard library that consists of many modules and packages that provide functionality for a wide range of tasks, such as working with files, networking, data manipulation, and more.

   Example: The `math` module is part of the Python standard library.

   ```python
   import math

   result = math.sqrt(25)
   ```

In summary, a module is a single file, a package is a collection of modules with a directory structure, and a library is a collection of modules or packages that provide reusable functionality. The distinction between them is mainly based on their organizational structure and scope.