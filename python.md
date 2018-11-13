

# Python
"Python is an interpreted high-level programming language for general-purpose programming."
- [Python Website](https://www.python.org/)

## Installing Python

Compared to Matlab and R, Python is fairly complicated to install and use, as it is general-purpose programming language.
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
# bash

python my_script.py
```

Command line applications can handle arguments in similar ways to linux cmd programs,

```
# bash

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

- [numpy](https://www.numpy.org/) - Fast numerical computation.
- [pandas](https://pandas.pydata.org/) - Advanced data structures.
- [jupyter-notebook](https://jupyter.org) - For running jupyter-notebooks.
- [scipy](https://www.scipy.org/) - Collection of packages for scientific computing.
- [scikit-learn](https://scikit-learn.org/) - Machine learning in python.
- [plotly](https://plot.ly/) - Interactive charts.
- [nPYc Toolbox](https://github.com/phenomecentre/nPYc-Toolbox) - NPC built toolbox for NMR and MS import, preprocessing, QC, and generating reports.

- [Numpy tutorial](https://docs.scipy.org/doc/numpy-1.15.1/user/quickstart.html)


- [Main page](https://github.com/csmsoftware/Programming-for-data-analysis-tutorial-Matlab-R-Python/blob/master/README.md)
