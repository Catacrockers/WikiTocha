[Back](https://github.com/Catacrockers/WikiTocha/blob/master/en/programming_languages/main.md)

# A guide for Python  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/2000px-Python-logo-notext.svg.png" alt="python" width="50"/>


Python interpreted language, Python has a design philosophy which emphasizes code readability and a syntax which allows programmers to express concepts in fewer lines of code. Exist 2 versions: Python 2.x and Python 3.x. Always write in version 3, v2 provide compatibility with version 3 and it is more reliable and maintainable.

Python is not a compiled programming language. A interpreter execute the program directly. It use dynamic memory, it can fail at execution in any moment if exist bug or unexpected results. Fortunately exist powerful IDEs and packages to help us to create working scripts.

If you are a python developer you need to set up your IDE, your environment, know how to search for packages and follow a Python coding convention.

## Pros of using Python

* It's platform independence.
* It's program size generate small executables.
* It has dynamic typing.
* It has dynamic scoping.
* Widely used, with a lot of APIs, including C/Cpp apis to improve performance.

## Cons of using Python

* It has not static type-checking.
* Interpreters can be susceptible to Code injection attacks.
* Just-in-time compilation provide a slower execution compared to direct native machine if no use C/Cpp libraries.

# Choose your IDE

Your python IDE must provide **IntelliSense** (code-completion aid), **linting** (checking the source code for programmatic as well as stylistic errors), **debugging**, **code-snippets**, **unit-testing** support, integration with **conda** and **environments**, a built in console and other tools you consider useful.

The IDEs I prefer for python are:

* Visual Studio Code
* Pycharm

## Visual Studio Code 
<img src="http://i.imgur.com/Rq9TURL.png" alt="vscode" width="50"/>


A short guide for installing and configuring [visual studio code for python](https://code.visualstudio.com/docs/languages/python). Also you can read this complete tutorial on [python development with visual studio code](https://realpython.com/python-development-visual-studio-code/) from [*real python*](https://realpython.com/).

1. **[Download](https://code.visualstudio.com/) Visual Studio Code**
2. **[Installation](https://code.visualstudio.com/docs/setup/linux)**
3. Add Visual Studio Code **extensions** for python:
   * **[Python extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-python.python)**: Linting, Debugging (multi-threaded, remote), Intellisense, code formatting, refactoring, unit tests, snippets, and more.
4. **[User Interface Guide](https://code.visualstudio.com/docs/getstarted/userinterface)**
5. **[User and workspace settings](https://code.visualstudio.com/docs/getstarted/settings)**
  

# Style

It is important to set a **coding convention** or **style guide** before you start developing. Some popular coding conventions are:

* [pep8](https://www.python.org/dev/peps/pep-0008/)
* [Google Style Guide](https://google.github.io/styleguide/pyguide.html)

The style guide must define the way you name projects, classes, functions and variables.

You can use [pylint](http://mascandobits.es/programacion/integracion-de-pylint/), to test your python scripts. This tool is designed for automating rules in style, so you don't have to manually revise the code.

# Virtual environments

Python can be used in a virtual environment like [Conda](https://conda.io/docs/index.html). The package manager allows to configure environments for projects with the packages you need.

## Install Conda
<img src="https://pbs.twimg.com/media/Clp3lTSUgAERFIt.png" alt="vscode" height="50"/>


Usually it will be enough with miniconda, as you can later download other packages. So you must follow these steps:
1. **[Download](https://conda.io/en/latest/miniconda.html) Miniconda**: For example python 3.7 for linux 64 [link](https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh)
2. **[Install miniconda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)**: Follow the instructions for your system and package.

## Conda cheatsheet

### **General**
Command | Description
-------- | -----------
```conda --version``` | Get the current version
```conda info```                                  | Verify conda is installed, check version 
```conda update conda```                          | Updates version if available
### **Managing environments**
Command | Description
-------- | -----------
``` create -n ENVIRONMENT python=2.7```  | Creates an environment for a python distribution
```conda install PACKAGENAME ```                  | Installs a package included in Anaconda
```source activate ENVIRONMENT  ```               | Activates environment
```source deactivate ENVIRONMENT```               | Deactivates environment
```conda env remove -n ENVIRONMENT  ```           | Removes environment
```conda env create -f env.yml  ```               | Load environment from a file
```conda env export > env.yml    ```              | Save current environment to a file
```conda env export -n ENVIRONMENT > env.yml```   | Save environment to a file
```conda env update < env.yml     ```             | Update current environment from file
```conda env update -n ENVIRONMENT < env.yml```   | Update environment from file
### **Managing packages**
Command | Description
-------- | -----------
```conda list     ```                             | View list of packages and versions installed in active environment
<code>conda list &#124; grep pytest</code>        | Check if pytest installed in current environment

Other conda cheatsheets:
* [kapeli cheatsheet](https://kapeli.com/cheat_sheets/Conda.docset/Contents/Resources/Documents/index)
* [ugo_py_doc cheatsheet](https://ugoproto.github.io/ugo_py_doc/JN_CS/)

# Find packages

One of the best things of Pyhton is the huge free software community it has. There is a package for everything in Python. You must learn to search for packages and test them. A good way is to use the [Awesome Python](https://github.com/vinta/awesome-python) github repo that contains a list of well-known packages organised by topics.

# Using C APIs

To use C libraries, [take a look](https://docs.python.org/3.6/extending/extending.html)

# Unit testing

* [Understanding Unit Testing](https://jeffknupp.com/blog/2013/12/09/improve-your-python-understanding-unit-testing/)
* [Unit test python guide](http://docs.python-guide.org/en/latest/writing/tests/)
* [Unit test reference](https://docs.python.org/3/library/unittest.html)

# Learning Python

You can learn python by programming, working on projects and of course improve your capabilities following tutorials. Bellow you will find a list of usefull python resources for learning.

* [Real python tutorials](https://realpython.com/)

# References

* [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), scripting language. Recommended for non-critical crossplatform algorithms.
* [Python guide](http://docs.python-guide.org/en/latest/), all info you need.
* [Pip](https://pypi.python.org/pypi/pip), the PyPA recommended tool for installing Python packages.
* [The zen of python](https://www.python.org/dev/peps/pep-0020/), Tim Peters recommends
* [Virtual environment](https://itsfoss.com/python-setup-linux/)
