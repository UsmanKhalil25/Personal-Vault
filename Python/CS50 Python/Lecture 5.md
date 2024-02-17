
- calculator.py
```python
def main():
	x= int(input("What's x? "))
	print("x squared is", square(x))

  

def square(x):
	return x*x

if __name__ == "__main__":
	main()
```

- test_calculator.py
```Python
def test_square():
	assert(square(2) == 4)
	assert(square(3) == 9)

if __name__ == "__main__":
	main()
	
```
- The naming convention for writing a test function is test_'function_name', similar is the case for the python file 
```Python
from calculator import square

  

def main():

test_square()

  

def test_square():

try:

assert(square(2) == 4)

except AssertionError:

print("2 squared was not equal to 4")

try:

assert(square(3) == 9)

except AssertionError:

print("3 squared was not equal to 9")

  

if __name__ == "__main__":

main()
```
- trying to catch assertErrors

#### pytest
```Python
from calculator import square
import pytest

def test_square():
	assert(square(2) == 4)
	assert(square(3) == 9)	
	assert(square(0) == 0)
	assert(square(-2) == 4)
	assert(square(-3) == 9)

def test_str():
	with pytest.raise(TypeError):
		square("cat")
		
```
- Use pytest to run the file it will automate the process of finding which test case is failing

```Python
def main():

name = input("What's your name? ")

hello(name)

  

def hello(name= "world"):

print("Hello,",name)

  

if __name__ == "__main__":

main()
```

```Python
from hello import hello

  

def test_hello():

assert(hello("Usman") == "Hello, Usman")
```
	Note that the hello() function is not returning anything (so it returns None by default) ans we are comparing if the value returned by hello("Usman") == "Hello, Usman" which is not true


## [Organizing Tests into Folders](https://cs50.harvard.edu/python/2022/notes/5/#organizing-tests-into-folders)

- Unit testing code using multiple tests is so common that you have the ability to run a whole folder of tests with a single command.
- First, in the terminal window, execute `mkdir test` to create a folder called `test`.
- Then, to create a test within that folder, type in the terminal window `code test/test_hello.py`. Notice that `test/` instructs the terminal to create `test_hello.py` in the folder called `test`.
- In the text editor window, modify the file to include the following code:
    
    ```
    from hello import hello
      
      
    def test_default():
        assert hello() == "hello, world"
      
      
    def test_argument():
        assert hello("David") == "hello, David"
    ```
    
    Notice that we are creating a test just as we did before.
    
- `pytest` will not allow us to run tests as a folder simply with this file (or a whole set of files) alone without a special `__init__` file. In your terminal window, create this file by typing `code test/__init__.py`. Note the `test/` as before, as well as the double underscores on either side of `init`. Even leaving this `__init__.py` file empty, `pytest` is informed that the whole folder containing `__init__.py` has tests that can be run.
- Now, typing `pytest test` in the terminal, you can run the entire `test` folder of code.