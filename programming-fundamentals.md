
# Programming fundamentals

In the introduction below, the syntax is python.

## Commands
Python, Matlab, and R are interpreted languages. That means the code is interpreted at run time (there's no pre-compiling).
Commands are given to the interpreter, either as a 'script', or in an interactive session.
The interpreter 'interprets' the code, translate it to binary CPU instructions, executes these instructions, and returns the result (if any).

## Variables & Datatypes
During execution, the instructions often need to access and manipulate data stored in memory.

Variables are named locations of the data in the memory, are of a specific 'datatype' have a value assigned to them.

### Simple datatypes

**String** - alphanumeric character lists, escaped by single or double quotes.

```
# python

print("John Smith")

# > John Smith
```

**Numeric** - Int, Float, Decimal, Double.

```
# python

print(20)

# > 20
```

**Boolean** - True/False

```
# python

print(True)

# > True
```

### Complex datatypes

* **Lists/Arrays** - An collection of other datatypes, indexed from 0 -> Infinity
* **Dictionaries/Hashes** - A collection of other datatypes, indexed with a string or numeric key.
*	**Matrices** - nD collections of datatypes.
*	**Tables** - 2D collections of objects with row and column indexes.
*	**Objects** - Predefined chunks of code with attached properties.

These datatypes can be defined in the code, and 'assigned' to variables.
These variables are the named location of this data in memory.

### String variable assignment
```
# python

my_name = "John Smith"
print(my_name)

# > John Smith
```

### Numeric variable assignment

```
# python

my_number = 20
print(my_number)

# > 20
```

## Operators

Operations can be carried out on variables, for example, adding 2 variables together.

```
# python

my_number = 20
my_other_number = 30
my_final_number = my_number + my_other_number
print(my_final_number)

# > 50
```

The + symbol is an example of an arithmetic operator, others include (`-`, `/` , `*`).
We've already seen the assignment operator (`=`).
We also have the relational operators for comparing values (`==`, `!=`, `<`, `>`),
and the logical operators (`&&`, `and`, `||`, `or`, `!`, `not`).

So, we've covered, datatypes, variables, and operations. Next is the conditionals.

## Conditionals

Conditions are way of creating a logical flow of operations through our program.
They use keywords like `IF`, `ELSE`, and `WHILE` to test conditions and execute different branches of code.

```
# python

threshold = 40
my_value = 24
if(my_value >= 40):
	print("Threshold passed")
else:
	print("Threshold not passed")

# > Threshold not passed
```

Conditionals can also be combined using logical operators:

```
# python

threshold = 40
my_value = 41
my_name = "John Smith"

if(my_value >= threshold and my_name == "John Smith"):
	print("Threshold passed by John Smith")
elif(my_value >= threshold)
	print("Threshold passed by " + my_name)
else:
	print("Threshold not passed")

# > Threshold passed by John Smith
```

Through the combination of variables, conditionals, and operators, more complex programs can be created.

## Iteration

In imperative languages, iteration is a process whereby blocks of code can be repeated.
In the code below, we set a counter, test its value, and if it's less than 5, we run the conditional block.
At the end of the block we increment the counter. This will result in the code being run 5 times.

```
# python

counter = 0
while(counter < 5):
	print(counter)
	counter = counter + 1

# > 0
# > 1
# > 2
# > 3
# > 4
```

## Functions

Functions are way of encapsulating code. This means they break your code up into functional units
that can be reused by different bits of code. Taking the previous example, we can encapsulate
the iterating counter printer into a function and call it to run the code.

```
# python

def print_number_of_times(times):
	counter = 0
	while(counter < times):
		print(counter)
		counter = counter + 1

number_of_times(4)

# > 0
# > 1
# > 2
# > 3
```

Functions have a name, and arguments. These arguments can be required or optional, can be
any datatype, and can have default values.

Functions can simply execute some code, or they can return values, and then can be called
in a nested format, whereby the output of one function becomes the input of another:

```
# python

def calculate_something(input1,input2):
	intermediate = input1 * input2
	return intermediate

print(calculate_something(3,6))

# > 18
```

### Variable Scope
Most languages have something called 'scope', which is where in the code the variables can be
accessed from. For example, a variable defined inside a function can only be accessed from within that function.

Variables which are accessible across the whole program are known as 'global variables',
and should generally be avoided where possible.


## Objects
Some languages (including Matlab, R, and Python), have support for object-orientation.
This is a way of grouping functions and variables of similar entities together in one place.
The definition of an object is a Class, and the instance of that Class is an object.
An objects functions are known as 'methods' and the variables are known as 'properties'.

## Control characters
Different languages use different 'control characters' for defining logical blocks executable code, for example separating out conditionals, operators, and function definitions.
In Matlab and R, some control characters used are the
`{}()[]`. In Python, indentation and `:` is used to specify logical blocks.

## Accessing data from disk
 Persistent data is data which when your program finishes (or crashes), still exists on disk.
 Persistent data can be read and written from various sources, including simple flat text files,
 including CSVs, XML or json, or more complex sources such as relational databases or online APIs.

 Flat files are opened with a file handle, and then operations are run with the file handle.

### Reading CSV

```
# python

import csv
with open('eggs.csv') as csvfile:
  spamreader = csv.reader(csvfile)
  for row in spamreader:
    print(', '.join(row))

# > Spam, Spam, Spam, Spam, Spam, Baked Beans
# Spam, Lovely Spam, Wonderful Spam
```

### Writing CSV

```
# python

import csv
with open('eggs.csv', 'w') as csvfile:
    spamwriter = csv.writer(csvfile)
    spamwriter.writerow(['Spam'] * 5 + ['Baked Beans'])
    spamwriter.writerow(['Spam', 'Lovely Spam', 'Wonderful Spam'])
```

Libraries and packages exist for reading and writing many file types and DB connections.
Another example of when google is your friend.

Carefully plan the format and structure of your data when designing your project
and writing your code. Most importantly, don't delete your raw data after you've processed it.

## Visualisation

When you are investigating your data, you will often want to plot the data.

Various charting libraries exist for most languages, each with different levels of functionality.
Some can produce very complex charts, but produce only static vector or bitmap images (ggplot2).
Others have less features but are interactive by default (plotly).

They generally work by providing vectors of information and various settings.

Some examples of these will be provided for each language.

## Help files
R and Matlab provide offline help files for understanding package functionalities and APIs.
Python's documentation is online, and packages often have readthedocs.io documentation pages.
Good documentation will give you an introduction to the package, argument settings,
and expected output. You should be able to drill down to to specific functions if
necessary. Learning how to read and interpret documentation will be necessary if you
plan to write any code beyond really basic stuff. Even then, most coders use google
for EVERYTHING.

## Managing code

So, you've taken the leap and started coding. How should you manage the code you write?
With version control! Version control enables you to 'version' your code and create 'branches'
for implementing new features, or enabling working with others on your code.
Git is a popular type of version control, and Github is a popular online Git repository.

The basic principle is, make changes to you code, 'commit' those changes,
and then 'push' those changes to the upstream repository (hosted for example on github).

### Initialising a repository
```
# bash

cd my_folder
git init
```

### Cloning out an existing repository

```
# bash

git clone [https://github.com/username/repository]
```

### Adding files.
```
# bash

git add . -A
```

### Commiting a change
```
# bash

git commit -m 'this is user-defined a comment to describe what is changing'
```

### Pushing the changes

```
# bash

git push
```

### Create a new branch and switch to it
```
# bash

git checkout -b [name_of_new_branch]
```

There are many features of git, however the above will get you most of the way.


## Packages
When someone or a group of people develop some code to achieve some purpose,
they might release it as a package. These packages can be installed and used
by you to perform the same task.

For example, Matlab provides many 'toolboxes', such as the 'Statistics and Machine Learning Toolbox'.
This package contains many functions for running statistical analyses.

In R, CRAN and Bioconductor are 2 large packaging systems for providing general purpose
analysis packages and bioinformatics specific packages.

In Python, packages can be installed from 'pip' or 'conda'.

In all 3 languages, 3rd party packages can also be installed from other sources.


## Setting up your environments

Firstly, you'll want to organise your code into a sane structure, with a
space dedicated to your coding and analysis projects. I use a folder in my home directory called 'workspace'.

```
~/workspace/
~/workspace/myproject/
~/workspace/myproject/data/
~/workspace/myproject/data/raw
~/workspace/myproject/data/processed
~/workspace/myproject/data/output
~/workspace/myproject/code/
~/workspace/myproject/code/r
~/workspace/myproject/code/matlab
~/workspace/myproject/code/python
~/workspace/myproject/env/
~/workspace/myproject/notebooks/
```

Good organisation of your workspace will enable you to write better code, with
less mistakes, and make it easier for you to come back in 6 months time and work
out what the hell was going on.


Keeping your data and code organised well will help you 6 months down the line.


[Matlab tutorial](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/blob/master/matlab.md)
