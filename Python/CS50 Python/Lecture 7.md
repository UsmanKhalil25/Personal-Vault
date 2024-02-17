#### Regular expressions
- A Regex, or Regular Expression, is **a sequence of characters that forms a search pattern**. Regex can be used to check if a string contains the specified search pattern.
#### Syntax
```Python
re.search(pattern,string,flags = 0)

```

#### Flags
- re.IGNORECASE
- re.MULTILINE
- re.DOTALL

#### Table for Regex
- . -> any character except newline
- * -> 0 or more repetitions
- + -> 1 or more repetitions
- ? -> 0 or 1 repetitions
- {m} -> m repetitions
- {m,n} -> m-n repetitions
- ^ -> matches the start of string
- $ -> matches the end of string or just before the newline at the end of the string
- [  ] - > set of characters
- [ ^ ] -> complementing the set
- A|B -> either A or B
- (...) -> a group
- (?....) -> non-capturing version
-  backslash d -> decimal digit
- backslash D -> not a decimal digit
- backslash s -> whitespace character
- backslash S -> not a whitespace character
- backslash w -> word character... as well as numbers and underscores
- backslash W -> not a word
```Python
import re
email = input("What's your email? ").strip()

if re.search(".+@.+",email):
	print("Valid")
else:
	print("Invalid")
```

- The above code checks if there is one or more characters before and after the @ sign
- It can also be done as follows
```Python
import re
email = input("What's your email? ").strip()

if re.search("..*@..*",email):
	print("Valid")
else:
	print("Invalid")
```


```Python
import re
email = input("What's your email? ").strip()
if re.search(r".+@.+\.com",email):
	print("Valid")
else:
	print("Invalid")
```
- In the above code we cannot use ".+@.+.edu" because the . in .edu means that it can be any character so this means ?edu will also be valid in this case
- Therefore we are to specify in our regular expression to use .edu which can be done by using escape character  "\.edu" inside of a raw str r""  
```Python
import re

email = input("What's your email? ").strip()
if re.search(r"^.+@.+\.com$",email):
	print("Valid")
else:
	print("Invalid")
```

```Python
import re

email = input("What's your email? ").strip()

if re.search(r"^[^@]+@[^@]+\.com$",email):
	print("Valid")
else:
	print("Invalid")
```

- lets breakdown the line -> r"^[^@]+@[^@]+\.com$"
	- r"" means that raw str is being used
	- the first ^ means start matching from the start of the string
	- [ ^@ ]+ means that all the characters but @ and the number of characters must be one or more

```Python
import re
email = input("What's your email? ").strip()

if re.search(r"^[a-zA-Z0-9_]+@[a-zA-Z0-9_]+\.com$",email):
print("Valid")
	else:
print("Invalid")
```

```Python
import re

email = input("What's your email? ").strip()
if re.search(r"^\w+@\w+\.(com|edu|net|gov|net)$",email):
	print("Valid")
else:
	print("Invalid")
```

```Python
import re

email = input("What's your email? ").strip()
if re.search(r"^\w+@(\w+\.)?\w+\.(com|edu|net|gov|net)$",email,re.IGNORECASE):
	print("Valid")
else:
	print("Invalid")

```
- the above code will work for an email such as l226873@lhr.nu.edu where there are two dots after the @ symbol
- there is still an issue what if there are more than 2 dots

```Python
import re

email = input("What's your email? ").strip()
if re.search(r"^\w+@(\w+\.)*\w+\.(com|edu|net|gov|net)$",email,re.IGNORECASE):
	print("Valid")
else:
	print("Invalid")

```



```Python
re.match(pattern,string,flags = 0)
re.fullmatch(pattern,string,flags = 0)
```
- No need to specify carrot symbol ^ in match as it automatically starts matching from the beginning of the string
- No need to specify carrot symbol ^ or dollar sign $ in fullmatch as it automatically starts matching from the beginning of the string till the end

```Python
import re

name =input("What's your name? ").strip()
matches = re.search(r"^(.+), (.+)$",name)
if matches:
	last,first = matches.groups()
	name = f"{first} {last}"
print(f"hello, {name}")
```

- the above code is used to match if the users enters his name as last-name, first-name
- we are storing in matches and then accessing  the groups which will contain the first and last-name
- 
```Python
import re

name =input("What's your name? ").strip()
matches = re.search(r"^(.+), (.+)$",name)
if matches:
	last= matches.group(1)
	first = matches.group(2)
	name = f"{first} {last}"
print(f"hello, {name}")
```

#### Walrus operator :=
```Python
import re
name =input("What's your name? ").strip()
if matches := re.search(r"^(.+), *s(.+)$",name):
	last= matches.group(1)
	first = matches.group(2)
	name = f"{first} {last}"
print(f"hello, {name}")
```
- this is also assigning the value to matches and also asking if matches is not none


```Python
url = input("URL: ").strip()


username =url.replace("https://twitter.com/","")
print(f"Username: {username}")
```

- in the above code we want to extract the username from their twitter url

```Python
re.sub(pattern,repl,string,count = 0,flags =0)
```
- pattern is the sequence of characters that we will search for
- repl is the replacement string that will be placed
- string is the string where we want the replacement to occur

```Python
import re
url = input("URL: ").strip()
username = re.sub(r"^(https?://)?(www\.)?twitter\.com/","",url)
print(f"Username: {username}")
```

```Python
import re
url = input("URL: ").strip()
if username :=re.search(r"^(https?://)?(www\.)?twitter\.com/(.+)$",url,re.IGNORECASE):
print(f"Username: {username.group(3)}")
```

```Python
import re
url = input("URL: ").strip()

if username :=re.search(r"^(?:https?://)?(?:www\.)?twitter\.com/(.+)$",url,re.IGNORECASE):
print(f"Username: {username.group(1)}")
```
- in the above code we used the non capturing groups (?: ...), this way we can use group(1) because it is not capturing the username only

```Python
import re

url = input("URL: ").strip()

if username :=re.search(r"^(?:https?://)?(?:www\.)?twitter\.com/([a-zA-Z0-9_]+)",url,re.IGNORECASE):
print(f"Username: {username.group(1)}")
```

```python
re.findall(pattern,string,flags = 0)
re.split(pattern,string,maxsplit = 0,flags = 0)
```
