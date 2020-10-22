# Lesson 1: The Command Line

## Objectives

1. Be familiar with the Command Line Interface
2. Compare the Windows and Linux  CLI
3. Perform basic Command Line operations using PowerShell in Windows and Terminal in Ubuntu

## What is the Command Line?

The command line is a powerful, text-based interface to your computer. As developers we will use it extensively throughout this course to install and configure the tools that we will need to build Web application including Python, Django, Git, etc. We'll also be using the command line to manage our Web application projects.

On Windows machines there are actually two built-in command shells: the **Command** shell and **PowerShell** with the latter being the more powerful of the two. In Ubuntu, you have the Gnome Terminal or simply **Terminal** which runs the Bourne Again Shell or **BASH** by default.

## How does the Command Line Works?

A command shell works like a language translator,  it accepts human readable commands and translates them into something the Operating System can read and process.

**Command Syntax**
**`command [ARGUMENT]...`**  

For example,

```bash
echo Hello
echo -n Hello
```

```powershell
Write-Host Hello
Write-Host Hello -Separator ";"
```

*Note!* In Linux, commands are case-sensitive, but in Windows, it is not. 

**Getting Help**

**`man COMMAND`**

For example, to know how the `pwd` command is used, type:

```bash
man pwd
```

## What Basic Commands Should You Know?

- **`ls`** (list files in your current directory)
	```bash
ls
ls ~
ls Desktop
ls -l Desktop
ls -l -h Desktop
ls -lh Desktop
ls D*
	```
*Note!* Both Windows and Linux, uses aliases for special directories such as root directory ( **`/`**),  user\'s home directory (**`~`**),  parent directory (**`..`** ) and  current directory (**`.`**). The asterisk (**\***) is a wildcard character which matches all strings
	
- **`cd`** (change directory)
	
	```bash
cd
cd Desktop
cd ~/Documents
cd ..
cd /
cd /var/www
	```
	*Note!* In Linux, forward slash (`/`) is used as a directory separator. Windows uses backslash (`\`) instead. 

	```powershell
	cd C:
	cd \
	cd \Users\
	```
	
- **`mkdir`** (make directory)
	```mkdir
mkdir CSDC105
mkdir CSDC105/Labs
mkdir 'Trends in Application Development'
mkdir -p ADNU/Classes/'First Sem'
	```

- **`rmdir`** (remove directory)
 	```bash
rmdir CSDC105/Labs
	```

- **`touch`** (create a file)
	```bash
touch README.md
	```
*Note!* Powershell does not have a `touch` command, but you can create an alias for the `New-Item` command.
	```powershell
Set-Alias touch New-Item
	touch README.md
	```
	
- **`cp`** (copy files and directories)
	```bash
cp README.md instructions.txt 
cp instructions.txt CSDC105/
cp instructions.txt CSDC105/ideas.html
cp -r CSDC105/ Desktop/ 
	```
	
- **`mv`** (rename files and directories)
	```bash
mv README.md INFO.txt 
mv INFO.txt CSDC105/
mv CSDC105/Labs CSDC105/Work 
	```

- **`rm`** (remove files and directories)
	
	```bash
rm instructions.txt
rm -f instructions.txt
rm -r -f CSDC105/Work
	```
	```powershell
rm instructions.txt
rm -Force instructions.txt
rm -Recursive -Force CSDC105/Work
	```

## Additional Commands

- **`>`** (output redirection)
	
	```bash
echo "Hello" > hello.txt
	```
	
- **`>>`** (output redirection, append)

	```bash
echo "Hi!" >> hello.txt
	```

- - **`|`** (pipe)
	```bash
cat hello.txt | grep "ello"
	```
	

*Note!* The `grep` command for pattern maching is only available in Linux

## Some Tips!

- You can change theme/look and feel of the Command Line

- In Linux, you can change your shell application (popular options include `csh`, `zsh`, `fsh`)

- You can also define aliases to the commands you use the most in BASH:
	
	```bash
alias ls="ls -lh"
ls
	```

- You may want to install a tiling Terminal application such as `tilix`

  	```bash
sudo apt install tilix
tilix
	```
	
	
	
	
	
	
	
	
	# Lesson 5: Modules

In this lesson you'll learn how to build your own custom Python module and use some useful modules part of the Python's very extensive standard library.

### What are modules?

One advantage of functions is the way they separate blocks of code from your main program. By using descriptive names for your functions, your main program will be much easier to follow. You can go a step further by storing your functions in a separate file called a **module** and then importing that module into your main program. An import statement tells Python to make the code in a module available in the currently running program file.

Storing your functions in a separate file allows you to hide the details of your program’s code and focus on its higher-level logic. It also allows you to reuse functions in many different programs. When you store your functions in separate files, you can share those files with other programmers without having to share your entire program. Knowing how to import functions also allows you to use libraries of functions that other programmers have written. 

There are several ways to import a module, and I’ll show you each of these briefly.

### Creating A Module

To start importing functions, we first need to create a module. A module is a file ending in **.py** that contains the code you want to import into your  program. Let's make a module that contains the functions `sayhi()`, `sayhello()` and `greet()`. To make this module, we'll remove from the file `hello.py` the function `sayhi()`, `sayhello()` and `greet()` and put it in a separate file named `greetings.py` in the same directory as `hello.py`:

```python
# filename: greetings.py

def sayhello():
    print("Hello, World!")
    
def sayhi(name):
    print("Hello, {}!".format(name))
    
def greet(name, message="Hello"):
    print("{}, {}!".format(message, name))
```

### Importing An Entire Module

To import functions contained a module, we use the `import` statement. The syntax for importing an entire module is as follows:

	import <module-name>

For example, in file `hello.py` we can import the entire `greetings` module via:


```python
# filename: hello.py
import greetings
```

When Python reads this file, the line `import greetings` tells Python to open the file `greetings.py` and copy all the functions from it into the `hello.py` program. You don’t actually see code being copied between files because Python copies the code behind the scenes just before the program runs. All you need to know is that any function defined in `greetings.py` will now be available in `hello.py.`


### Calling a Function Defined inside a Module

To call a function from an imported module, enter the name of the module you imported, followed by the name of the function, separated by a dot.

```python
# filename: hello.py

greetings.sayhello()
```

```python
# filename: hello.py

greetings.sayhi("Juan")
```

### Importing Specific Functions
You can also import a specific function from a module. Here's the general syntax for this approach:

	from <module-name> import <function-name>

With this syntax, you don't need to use the dot notation when you call a function. Because we've explicitly imported the function in the import statement, we can call it by name when we use the function.

```python
# filename: hello.py

from greetings import sayhi

sayhi("Juan")
```

You can import as many functions as you want from a module by separating each function’s name with a comma.

	from <module-name> import <function1-name>, <function2-name>

```python
# filename: hello.py

from greetings import sayhello, sayhi, greet

sayhello()
sayhi("Pedro")
greet(message="Kumusta", name="Tiago")
```

### Importing All Functions in a Module

You can tell Python to import every function in a module by using the asterisk (`*`) operator:

```python
# filename: hello.py

from greetings import *

sayhello()
sayhi("Pedro")
greet(message="Kumusta", name="Tiago")
```

The asterisk in the import statement tells Python to copy every function from the module greetings into this program file. Because every function is imported, you can call each function by name without using the dot notation. However, it’s best not to use this approach when you’re working with larger modules that you didn’t write: if the module has a function name that matches an existing name in your project, you can get some unexpected results. Python may see several functions or variables with the same name, and instead of importing all the functions separately, it will overwrite the functions.

The best approach is to import the function or functions you want, or import the entire module and use the dot notation. This leads to clear code that's easy to read and understand.

### Using `as` to Give a Function an Alias

If the name of a function you're importing might conflict with an existing name in your program or if the function name is long, you can use a short, unique **alias** - an alternate name similar to a nickname for the function. You'll give the function this special nickname when you import the function. Below is such an example:

```python
# filename: hello.py

from greetings import greet as g

g(message="Mabuhay", name="Mateo")
```

The import statement shown above renames the function `greet()` to `g()` in the `hello.py` program. Any time we want to call `greet()` we can simply write `g()` instead, and Python will run the code in `greet()` while avoiding any confusion with another `greet()` function which might exist in `hello.py` program.

### Using `as` to Give a Module an Alias

You can also provide an alias for a module name. Giving a module a short alias, like `gt` for `greetings`, allows you to call the module's functions more quickly.

Calling `gt.greet()` is more concise than calling `greetings.greet()`:

```python
# filename: hello.py

import greetings as gt

gt.greet(message="Mabuhay", name="Mateo")
```

### Checking if a Module is Being Executed

When a module is being imported into another module, not only will its various function be imported but its top-level code will also be executed. For example, if we have a statement calling the `sayhello()` function in `greetings.py`, this statement will be executed (and hence its outputs will be displayed) whenever the `greetings` module is imported in another module or program.

```python
# filename: greetings.py

def sayhello():
    print("Hello, World!")
    
def sayhi(name):
    print("Hi, {}!".format(name))
    
def greet(name, message="Hello"):
    print("{}, {}!".format(message, name))
    
sayhello()
```

    Hello, World!



```python
# filename: hello.py

import greetings as gt

gt.greet(message="Magandang araw", name="Lukas")
```

    Hello, World!
    Magandang araw, Lukas!


To avoid running the top-level code, we can perform a check if the module is being run directly. This can be done by checking the value of the `__name__` variable. The `__name__` is a special built-in Python variable which evaluates to the name of the current module. However, if a module is being run directly (from command line), then `__name__` instead is set to the string `"__main__"`.


```python
# filename: greetings.py

def sayhello():
    print("Hello, World!")
    
def sayhi(name):
    print("Hi, {}!".format(name))
    
def greet(name, message="Hello"):
    print("{}, {}!".format(message, name))
   
if __name__ == "__main__":
    sayhello()
```

The `if` test in the code above will ensure that the `sayhello()` function will be called only when we are executing the `greetings` module directly from the command-line and not whenever we're simply importing its code to another module.

### Python Standard Modules

Python's standard library is very extensive, offering a wide range of functionalities. See the documentation here: https://docs.python.org/3/library/index.html


#### The `math` Module
For example, the `math` module provides access to the mathematical functions defined by the C standard.
Some of the most commonly used functions of the module are: 
- `sqrt(x)`: Return the square root of `x`. 
- `ceil(x)`: Return the ceiling of `x`, the smallest integer greater than or equal to `x`. 
- `floor(x)`: Return the floor of `x`, the largest integer less than or equal to `x`. 
- `factorial(x)`: Return `x` factorial. 
- `pow(x,y)`: Return `x` raised to the power `y` 
- `pi`: This is actually a the mathematical constant $\pi$ = 3.141592…, to available precision. 


```python
import math
print(math.sqrt(16))
print(math.ceil(3.14))
print(math.floor(3.14))
print(math.factorial(4))
print(math.pow(2.0,16))
print(math.pi)
```


#### The `random` Module
There's also a `random` module which implements pseudo-random number generators for various distributions.
Some of the most commonly used functions of the module are: 
- `randint(a, b)`: Return a random integer `x`, which belongs to the range `[a,b]`. 
- `choice(seq)`: Return a random element from the non-empty sequence `seq`. 
- `shuffle(x)`: Shuffle the sequence `x` in place.

```python
import random
print(random.randint(1,10))
print(random.choice(['H','T']))
numbers = [x for x in range(5)]
random.shuffle(numbers)
print(numbers)
```


#### The `os` Module

There's even an `os` module which provides a portable way of using operating system dependent functionality. Some of the functions that we might need from this module are as follows:
- `os.getcwd()`: Return a string representing the current working directory.
- `os.listdir(path)`: Return a list containing the names of the entries in the directory given by path'
- `os.path.basename(path)`: Return the base name of pathname path
- `os.path.join(path, *paths)`: Join one or more path components intelligently


```python
import os
print(os.getcwd())
print(os.listdir("."))
print(os.path.basename("~/Documents/file.txt"))
print(os.path.join("~","source.py"))
```
