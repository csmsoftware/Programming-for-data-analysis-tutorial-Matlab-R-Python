
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

![Matlab figure 1](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/matlab-figure-1.png "Matlab figure 1")

These commands could be typed individually into the command prompt, or equally saved into a script so that all of the commands can be run together.  To plot the cosine of x as well, we can run the following commands:

```
% matlab

hold on;
h2 = plot(x,cos(x),'Color','red','LineStyle','--','LineWidth',2);
```

![Matlab figure 2](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/matlab-figure-2.png "Matlab figure 2")

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

![Matlab figure 3](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/raw/master/img/matlab-figure-3.png "Matlab figure 3")

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
c(2,1)([1 6 4 end-2 13]) % this will fail!
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
