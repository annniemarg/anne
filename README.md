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
	
	
	
	
	# Lesson 4: Functions

## What are functions?

Functions are named blocks of code that are designed to do one specific job.

Functions are useful if you need to perform a task multiple times throughout your program You don't need to type all the
code for the same task again and again; you just call the function dedicated to handling that task.

### Function Definition

#### *Syntax*
	def <function-name> ( <parameter-list> ):
	   →| <block-statement(s)> 
A function definition begins with the keyword `def`. This tells the Python interpreter that you're defining a function.

Written in the function header is the name of the function and, if applicable, the information the function needs to do its job. The parentheses hold that information. 

Below are two simple examples of a function definition. The function `sayhello()` needs no information to do its job. Hence, the empty parentheses. Note! The parentheses are required in the function definition. 

The function header ends in a colon.

Any indented lines that follow the function header make up the body of the function.


```python
def sayhello ():
    print("Hello, World!")
```


```python
def sayhi(name):
    print("Hi, {}!".format(name))
```

### Function Call

When you want to use this function, you call it. A function call tells Python to execute the code in the function. To call a function, you write the name of the function, followed by any necessary information in parentheses. 

#### *Syntax*
	<function-name> ( <argument-list> )

#### 


```python
sayhello()
```

    Hello, World!



```python
sayhi("Glenn")
```

    Hi, Glenn!


### Arguments vs Parameters

The variable `name` in the definition of `sayhi()` is an example of a **parameter**, a piece of information the function needs to do its job. 

The value `'Glenn'` in `sayhi('Glenn')` is an example of an **argument**. An argument is a piece of information that’s passed from a function call to a function.


### Positional Arguments
When you call a function, Python must match each argument in the function call with a parameter in the function definition. 

The simplest way to do this is based on the order of the arguments provided. Values matched up this way are called **positional arguments**.

*Important!* Order matters in positional arguments. You can get unexpected results if you mix up the order of the arguments in a function call when using positional arguments.


```python
def greet(message, name):
    print("{}, {}!".format(message, name))
```


```python
greet("Kumusta", "Juan")
```

    Kumusta, Juan!



```python
greet("Juan", "Kumusta")
```

    Juan, Kumusta!


### Keyword Arguments
A **keyword argument** is a name-value pair that you pass to a function. You directly associate the name and the value within the argument, so when you pass the argument to the function, there's no confusion. 

Keyword arguments free you from having to worry about correctly ordering your arguments in the function call, and they clarify the role of each value in the function call.


```python
greet(message="Kumusta", name="Juan")
```

    Kumusta, Juan!



```python
greet(name="Juan", message="Kumusta")
```

    Kumusta, Juan!


### Default Values

When writing a function, you can define a default value for each parameter. If an argument for a parameter is provided in the function call, Python uses the argument value. If not, it uses the parameter's default value.

Using default values can simplify your function calls and clarify the ways in which your functions are typically used. When you define a default value for a parameter, you can exclude the corresponding argument you'd usually write in the function call. 


```python
def greet(name, message = "Hello"):
    print("{}, {}!".format(message, name))
```

*Important!* When you use default values, any parameter with a default value needs to be listed after all the parameters that don't have default values. 


```python
greet(name="Juan")
```

    Hello, Juan!



```python
greet(name="Juan", message="Annyeonghaseyo")
```

    Annyeonghaseyo, Juan!


### Return Values
A function doesn't always have to display its output directly. Instead, it can process some data and then return a value or set of values. The value the function returns is called a **return value**. The return statement takes a value from inside a function and sends it back to the line that called the function. Return values allow you to move much of your program's grunt work into functions, which can simplify the body of your program.


```python
def full_name(first_name, middle_name, last_name):
    complete_name = "{} {} {}".format(first_name, middle_name, last_name)
    return complete_name.title()
```


```python
black_mamba = full_name ("kobe", "bean", "bryant")
print(black_mamba)
```

    Kobe Bean Bryant

To compute the area of a circle using the formula:
$$ A = \pi r^2$$
where $r$ is the radius


```python
def area_circle (radius):
    area = 3.14 * radius ** 2
    return area
```


```python
a = area_circle(3)
print(a)
```

    28.26


To manually compute the remainder when dividing two numbers:


```python
def remainder(n, m):
    while n > m:
        n = n - m
    return n
```


```python
result = remainder(4, 10)
print(result)
```

    4


To compute the average value given a list of numbers.


```python
def compute_average_v1(values):
    total = 0
    for v in values:
        total += v
    return total / len(values)
```


```python
grades = [98, 97, 86, 100, 68]
ave_grade = compute_average_v1(grades)
print(ave_grade)
```

    89.8

### Passing an Arbitrary Number of Arguments
Sometimes you won't know ahead of time how many arguments a function needs to accept. Fortunately, Python allows a function to collect an arbitrary number of arguments from the calling statement using the **splat** operator.

In the definition of function `compute_average_v2()` below, the asterisk in the parameter `*values` tells Python to make an empty tuple and pack whatever values it receives into this tuple. 

```python
def compute_average_v2(*values):
    total = 0
    for v in values:
        total += v
    return total / len(values)
```


```python
print(compute_average_v2(98, 90))
```

    94.0



```python
print(compute_average_v2(98, 90, 100))
```

    96.0


*Important!* If you want a function to accept several different kinds of arguments, the
parameter that accepts an arbitrary number of arguments must be placed
last in the function definition.  Python matches positional and keyword
arguments first and then collects any remaining arguments in the final
parameter.


```python
def show_record_v1(name, *grades):
    print("{}'s Grades:".format(name))
    for g in grades:
        print(g)
```


```python
show_record_v1("John", 90, 95, 98)
```

    John's Grades:
    90
    95
    98



```python
show_record_v1("Mark", 98, 93, 97, 99)
```

    Mark's Grades:
    98
    93
    97
    99


Also, sometimes you'll want to accept an arbitrary number of arguments, but you won’t know ahead of time what kind of information will be passed to the function. In this case, you can write functions that accept as many key-value pairs as the calling statement provides.

The definition of `show_record_v2()` below expects a name, and then it allows the user to pass in as many name-value pairs as they want. The double asterisks before the parameter `**grades` cause Python to create an empty dictionary called `grades` and pack whatever name-value pairs it receives into this dictionary. Within the function, you can access the key-value pairs in `grades` just as you would for any dictionary.

```python
def show_record_v2(name, **grades):
    print("{}'s Grades:".format(name))
    for subject, grade in grades.items():
        print(subject, grade, sep=" = ")
```


```python
show_record_v2("Luke", english=95, art=98, religion=89)
```

    Luke's Grades:
    english = 95
    art = 98
    religion = 89


### Built-in Functions

The Python interpreter has a number of functions and types built into it that are always available. Here are some examples:

To get the absolute value of a number:


```python
abs(-123.45)
```


    123.45



To convert an integer number to a binary string:


```python
bin(4)
```


    '0b100'



To get the largest item in an iterable or the largest of two or more arguments:


```python
max(9, 1, 2020)
```


    2020




```python
max([9, 1, 2020])
```


    2020



To get the minimum:


```python
min(9, 1, 2020)
```


    1




```python
min([9, 1, 2020])
```


    1



To round numbers two within a specific precision:


```python
round(3.1415926, ndigits=2)
```


    3.14



To sort a list:


```python
grades = [98, 97, 86, 100, 68]
sorted(grades)
```


    [68, 86, 97, 98, 100]



To compute the sum of the elements in a list:


```python
sum(grades)
```


    449



See https://docs.python.org/3/library/functions.html for more details.
	
	
	
	
	
	
	
	
	
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
