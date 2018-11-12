# Programming for data-analysis; An introduction to Python, Matlab, and R.

This is a gentle introduction to programming for data analysis.
The concepts presented here will be new for some of you, or you may already be well versed in coding.
 Either way it should hopefully get all of you to the stage where you can install and use one
 or more of these languages for your own data analysis needs.

There is no way we can teach you everything about coding in 2 hours, however we can
give you the basic knowledge you will need to get started, and point you in the right direction for learning more.

So, we're going to cover coding basics, how to organise your work, some of the main
packages used by the different languages for things such as charting and data analysis.

At some point in your training or work, you will have come across one or more of the
languages we will be discussing today, Matlab, R, and Python.

Each of these languages provide many of the features required to achieve the aims of your
analysis, and the choice of them generally boils down to personal preference,
what your supervisor or tutor used, and what packages are available for the language.
Matlab is used heavily in engineering disciplines, R is primarily a statistics language,
and Python is a general purpose language with many packages for scientific computing.

Despite their differences, in terms of data analysis, any of these will ultimately achieve
your aims of opening and processing your data, analysing it, and recording the results somewhere.
That's because all of these languages and packages utilise and are built on the same
programming fundamentals, which we're now going to go through.

# General introduction

In the introduction below, the syntax is python.

## Commands
Python, Matlab, and R are interpreted languages. That means the code is interpreted at run time (there's no pre-compiling).
Commands are given to the interpreter, either as a 'script', or in an interactive session.
The interpreter 'interprets' the code, translate it to binary CPU instructions,
executes these instructions, and returns the result (if any).

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
In the code below, we set a counter, test it's value, and if it's less than 5, we run the conditional block.
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

## Accessing data
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

https://plot.ly/python/

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

# Matlab

Matlab is a propriety computational environment developed by Mathworks.

### Installing Matlab

Matlab can be installed from the college central software repository

[Imperial Matlab Installation](https://uk.mathworks.com/academia/tah-portal/imperial-college-london-600177.html)

- Click 'Get started today'
- Sign in with your college account.
- Register with Mathworks (linking your college account with the Mathworks account).
- Download Matlab.
- Run the installer, specifying the email address you used when registering your Mathworks account.
- When installing, you have the option to install whichever toolboxes you require. These toolboxes can be installed later by navigating to the Add-Ons on the Home tab.


### Intro to Matlab
The interface provides windows to various views of your code and data,
such as current variables, text editor for code, and a built-in debugger
with code inspection.

![Matlab IDE](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/matlab-example.jpg "Matlab IDE")

### Installing packages
Matlab will look in a set of default folders for functions/packages so if you want to install new packages, you will need to tell Matlab where to look.  This default path can be found by clicking on the 'Set Path' button in the Home tab (see Environment) and you can manually add folders to the path here.  Alternatively, you can navigate to a particular folder in the user the path bar towards the top of the working environment.  The 'Current Folder' window shows you the contents of the selected folder.  The contents of this folder can be called in Matlab, although functions within folders typically cannot (these are likely to be shown with greyed-out file names).  To ensure that all functions within a folder are available for Matlab to run, you should run the following command:

```
% matlab

addpath(genpath(pwd));
```
Following the execution of this command, all functions within all subfolders should be able to called from Matlab.  You will have to repeat this step each time you open Matlab, unless you change the default path using the 'savepath' function or the 'Set Path' window.

Any Matlab toolboxes that you have installed will be automatically added to the path.

### Commands, scripts and functions
You can type commands directly into the command window which will be executed immediately after 'Return' is pressed.  The results will be displayed to screen and variables created will be visible in the workspace browser.  Terminating each command with a semicolon suppresses the output being displayed to screen.  The following example generates a vector of data from 0 to 3pi with increments of pi/10.  The sine of this vector is calculated and then plotted.

```
% matlab

x = 0:pi/10:3*pi;
y = sin(x);
figure;
h1 = plot(x,y,'Color','blue');
xlabel('x','FontSize',16);
ylabel('f(x)','FontSize',16);
box on;
```

![Matlab figure 1](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/matlab-figure1.png "Matlab figure 1")

These commands could be typed individually into the command prompt, or equally saved into a script so that all of the commands can be run together.  To plot the cosine of x as well, we can run the following commands:

```
% matlab

hold on;
h2 = plot(x,cos(x),'Color','red','LineStyle','--','LineWidth',2);
```

![Matlab figure 2](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/matlab-figure2.png "Matlab figure 2")

The 'hold' command is required to prevent the plotting of the cosine wave overwriting that of the sine wave.  If, instead, you wanted to draw the cosine in a separate graph, then first create a new empty figure.

To include a legend and change the appearance of the axes labels, you could run the following commands.  Note that the command 'gca' is asking Matlab to change the current axes (i.e. most recently drawn/clicked in):

```
% matlab

% Add a legend and increase its font size
legend([h1 h2],{'sin(x)','cos(x)'},'FontSize',18);

% Change the xy-axes' font size, and the x-axis' ticks and labels
set(gca,'FontSize',14,...
    'XTick',0:pi:3*pi,...
    'XTickLabel',{'0','\pi','2\pi','3\pi'});

% Change the x-axis' limit
xlim([0 3*pi]);
```

![Matlab figure 3](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/matlab-figure3.png "Matlab figure 3")

Functions take inputs and typically produce outputs, and a simple function is shown below.  Note the use of (square) brackets for grouping the output arguments and the parentheses for grouping the input arguments:

```
% matlab

function [ sumD,sumOD ] = magicMatrix(n)
% magicMatrix - generate 'magic' matrices of size nxn and calculate the
% row, column and diagonal sums

% Generate the matrix
m = magic(n)

% Summation of rows
sumR = sum(m,1)

% Summation of columns
sumC = sum(m,2)

% Diagonal sum?
d = eye(n) == 1
sumD = sum(m(d))

% What about the other diagonal?
od = flipud(d)
sumOD = sum(m(od))

end
```

### Logical statements and loops
The following function gives an example of an if/elseif/else statement, a for loop and a while loop.  Note that the indentation is not crucial, unlike in Python.  'If' statements can contain any number of 'elseif' elements (i.e. from 0 upwards) but note that if more than one conditional statement is true, then only the first of these will be executed.

If a 'for' loop, the number of iterations performed will depend on the number of elements formed in the 'n = 1:2:11' notation.  In this example, 1:2:11 will result in 6 iterations of n = [1 3 5 7 9 11].  Note that omission of the central number will result in increments of 1, such that 'n = 0.5:5' results in 'n = [0.5 1.5 2.5 3.5 4.5]'.

While loops have the potential to continue infinitely, so be sure that the logic behind them is sound.

```
% matlab

function logicalExamples(x,y)
%logicalExamples and loops

if x == y

    disp('x and y are the same');

elseif x < y

    disp('x < y');
    for n = x:1:y        
        disp(num2str(n));        
    end

else
    % So this must be the case where x > y
    disp('x > y');

    while x > y
        x = x - 1;
        disp(num2str(x));
    end

end

end
```

Having saved this function, you can run it:

```
% matlab

logicalExamples(10,15);
logicalExamples(5.5,5.5);
logicalExamples(20,10.2);
```

Note that Matlab is case sensitive so ensure that you replicate the function names exactly as they are saved.

### Data types
Matlab has a lot of data types which can be confusing, especially as some respond differently depending on whether you should use () or [] or {}.

All numerical entities are by default saved as n-dimensional arrays.  The command:

```
% matlab

r = rand(4,3,2);
```

creates an array of random numbers with 4 rows, 3 columns and 2 pages.  You can access specific parts of that array using the following commands:

```
% matlab

r(:,:,1) 		% just the first page, but all rows and columns of it
r(:,1,:) 		% all rows of the first column, in both pages
r([2 4],[1 3],2) 	% rows 2 and 4, columns 1 and 3, but of only page 2
```

To access certain parts of an array, we use parentheses.  The colon operator represents 'all', so replaces the need to type 1:4 to access all rows of r.  Square brackets are used to create a vector to group indices together, such as:

```
% matlab

b = [2 4];
c = [1 3];
r(b,c,2)
```

To create you own matrix, remember that new rows are delineated by semicolons and columns can optionally be separated by commas.  Note that Matlab isn't fussy about spacings between semicolons and commas:

```
% matlab

mm = [1 2 3; 4 5 6;7,8,9]
```

Text is typically represented in 2 ways in Matlab: either as a string or as part of a cell array.  Strings are simpler and are just typed between speech marks, such as:

```
% matlab

s = 'This is a string'
```

To access individual elements within this string, the following commands might be useful:

```
% matlab

s(2)
s(1:6)
s(end-2:end)
```

Using the comma/semicolon notation and braces, we can make a cell array of text:

```
% matlab

c = {'This is a cell','So is this';'And this is another','And another'}
```

Matlab is storing the 4 strings in a cell array (i.e. an array of individual cells).  We can access each cell by using the conventional parentheses () or we could access the string itself by using the braces {}.  Run the following examples, and note how the output is different:

```
% matlab

c(1,1)
c{1,1}
c{2,1}([1 6 4 end-2 13])
c{2,1}([1 6 4 end-2 13]) % this will fail!
```

Cells can also be used to store a mixture of text and numeric values:

```
% matlab

d = {'x1',1,1,1;'x2',2,4,8;'x3',3,9,27;'x4',4,16,64}
```

Note, however, that when stored in a cell array numeric values do not behave as if they were in a regular array.  To plot the numeric parts, use the 'cell2mat' function, such as:

```
% matlab

figure;
hold on;
h1 = plot(cell2mat(d(:,2)),cell2mat(d(:,3)),'-bo');
h2 = plot(cell2mat(d(:,2)),cell2mat(d(:,4)),'-rx');
legend([h1 h2],{'x^2','x^3'},'Location','northwest');
set(gca,'FontSize',16);
```

Large amounts of numeric data are not suited for storage in a cell array. Instead, they should be stored in a regular array.  When dealing with a range of datatypes, such as patient metadata which contains text (ID, status, disease, etc) and numeric values (weight, height, age, etc) then cell arrays are ideally suited.

### Halting execution
If for whatever reason you wish to halt the execution of a current function, then you can press

```
Ctrl + C
```
which will halt execution at the next function.  Note that any currently running functions will complete, which explains why force quitting is not always instantaneous.  You can also press these buttons to halt the output being printed in the command window.

### Documentation
The documentation for a particular function can be displayed in the Matlab command prompt by running the following command:

```
% matlab

help str2num
```

Alternatively, there is an interactive documentation browser which can be accessed by typing either:

```
% matlab

doc
```

for general enquiries, or more specifically for a single function:

```
% matlab

doc str2num
```

Web documentation tends to mirror what is available in the native doc browser, and a lot of questions have been asked and answered on Stack Exchange, Matlab Central and Matlab File Exchange.

### Useful packages
When installing Matlab, a lot of the toolboxes that are available are unlikely to be useful.  As a minimum, you should be installing the following:
- Bioinformatics Toolbox
- Image Processing Toolbox
- Statistics and Machine Learning Toolbox

# R
"R is a free software environment for statistical computing and graphics."
- [r-project.org](https://www.r-project.org/)

## Installing R

R can be run from the command line, however we are going to use RStudio, a free-to-use program that provides a user-friendly environment. RStudio interface is based on similar scheme of others scripting languages, such as Spyder for Python or Matlab.

The latest version of R can be downloaded from the [CRAN website](https://cran.r-project.org), whereas R Studio can be found on the [RStudio website](https://www.rstudio.com).

R must be installed before RStudio.

### Intro to R Studio

RStudio default layout consists of three panels. At left there is a panel showing the code executed plus eventually the textual output. At right, the top panel show the current variables/functions loaded in the environment (top) and the bottom panel allows the access to the file system. When a script is opened the left panel is split in two.

v

### Installing packages

R software packages are distributed through three main channels: CRAN, Bioconductor and Github.

CRAN packages can be installed directly from the command line, by calling the function:
```
# R

install.packages
```
For example, to install the package ```ggplot2```:
```
# R

install.packages('ggplot2')
```
or, equivalently,
```
# R

install.packages("ggplot2")
```
Please notice that the name of package is passed to the function as a string through the characters ```"``` or ```'``` (they are exchangeable in R).

Typically, the function will install also all the dependencies, but in some cases they must be installed manually. This is usually reported in the output generated by ```install.packages```.

To install Bioconductor packages, first install the ```BiocManager``` package:
```
# R

if (!requiredNamespace("BiocManager"))
    install.packages("BiocManager")
```
then call the actual install command (e.g. to install the ```GenomicFeatures``` package):

```
# R

BiocManager::install("GenomicFeatures")
```

Github packages are directly distributed by the developers, and may contain features still in development, so users should ensure that the code works properly before applying it to real-case problems.
To install packages from Github, it is necessary to know the URL of the package. These can be found by searching the name of the package on Github website. For instance, the URL for the ```MALDIquant``` package is

[https://github.com/sgibb/MALDIquant](https://github.com/sgibb/MALDIquant)

The package ```devtools``` (from CRAN) is required to install packages from Github:

```
# R

install.packages("devtools")
```

Then install the package, calling the command:
```
# R

devtools::install_github("<DeveloperName>/<PackageName>")
```

that in the case of ```MALDIquant``` becomes

```
# R

# URL: https://github.com/sgibb/MALDIquant =
#      https://github.com/<DeveloperName>/<PackageName>

devtools::install_github("sgibb/MALDIquant")
```

**Resources:**

- [CRAN website](https://cran.r-project.org)
- [Bioconductor website](https://bioconductor.org)
- [Github website](https://github.com)

### Documentation

R base and packages functions are distributed with a help that also shows examples of usage.
The help can be called by the command (to be exectuted in the command line):
```
# R

?<functionName>
```
For instance, to get the help associated with the function ```factor```:
```
# R

?factor
```
Additional information is often provided together with packages on their website. Simple tutorials may be distributed as well, called *vignette*.

### Useful packages

- ggplot2
- deplyR
- tidyR
- XCMS - MS import and preprocessing.

# Python
"Python is an interpreted high-level programming language for general-purpose programming."
- [Python Website](https://www.python.org/)

## Installing Python

Python is a bit more complicated, as it is general-purpose programming language.
The situation is made more complicated by different versions (2.x vs 3.x), and different package managers.

### Virtualenv

Virtualenv is the recommended approach to handling multiple installations of python on your system. Each python script or tool you use may require different versions of python, or different packages, or different versions of packages. Virtualenv is a way of seperating out these differences to resolve conflicts. Typically you would use a different virtual environment for each project you use. The following bash shell commands create a new virtual environment and then activate it for dynamic usage - all python commands entered after activate has run will use the python kernel from the virtual environment.

```
# bash
virtualenv ~/venv/[myenv]
source ~/venv/[myenv]/bin/activate
```

You can also access the virtualenv python binaries directly with:

```
# bash
~/venv/[myenv]/bin/python3
```

### Pip Packages
pip is the main python package management system. It's used for installing packages into the python kernel, which can then be imported from within the scripts.

```
# bash
pip install numpy nPYc
```

### Conda on Windows

On Windows, conda is the simplest package management system to use. It uses the Anaconda navigator to explore and configure environments.

- [Anaconda website](https://www.anaconda.com/)
- [Getting started with Anaconda Navigator](https://docs.anaconda.com/anaconda/user-guide/getting-started/)




### The basic console

Once installed, python can be run in an interactive console mode, by simply running `python` from
the command line. In console mode, python can be entered and executed line by line.

![Example Python Console](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/python-console.png "Python console")

Python can also run 'scripts', text files containing python code. Name these file `*.py`, and run them as follows:

```
python my_script.py
```

Command line applications can handle arguments in similar ways to linux cmd programs,

```
python my_script.py -a arg1 -b arg2 -c arg3
```

### IPython QT Console

The IPython QT Console is an QT GUI version of the basic console. It supports embedded charts and interactive elements.

- [IPython QT Console](https://ipython.org/ipython-doc/3/interactive/qtconsole.html)

![Example IPython QT Console](https://ipython.org/ipython-doc/3/_images/qtconsole.png "IPython QT Console")


### Spyder IDE
Spyder is an interactive python environment similar to R Studio and Matlab.

- [Spyder IDE](https://www.spyder-ide.org/)

![Example Spyder IDE](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/Spyder-windows-screenshot.png "Spyder IDE")

### Jupyter/IPython Notebook
Jupyter Notebooks (previously called IPython Notebooks) are another widely-used interactive python environment that enable you to mix code and markdown to create, save,
and share data analysis workbooks.

You are able to use Python kernels, R environments, Julia, and a wide-range of community supported kernels.

Each 'cell' contains either markdown, code, or plain text, and cells can be executed individually or sequentially.

Notebooks can be saved as json and exported and imported by other users.

- [Jupyter Notebooks](https://jupyter.org/)
- [Community supported kernels](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels)

![Example Jupyter Notebook](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/example-notebook.png "Jupyter Notebook")


### Useful Packages

**numpy - Fast numerical processing.
**pandas - Table data structures.
**jupyter-notebook - For running jupyter-notebooks.
**scipy - Wide range of packages for scientific computing.
**scikit-learn - Machine learning in python.
**plotly - Interactive charts.
**nPYc Toolbox - NPC built toolbox for NMR and MS import, preprocessing, QC, and generating reports.
