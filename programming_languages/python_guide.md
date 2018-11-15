# A guide for Python

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

Your python IDE must provide IntellinSense, linting, debugging, a built in console and other tools you consider useful.

The IDEs I prefer for python are:

* Visual Studio Code
* Pycharm

# Style

It is important to set a **coding convention** or **style guide** before you start developing. Some popular coding conventions are:

* [pep8](https://www.python.org/dev/peps/pep-0008/)
* [Google Style Guide](https://google.github.io/styleguide/pyguide.html)

The style guide must define the way you name projects, classes, functions and variables.

You can use **pylint** for automating rules in style, so you don't have to manually revise the code.

# Virtual environments

Python can be used in a virtual environment like [Conda](https://conda.io/docs/index.html). The package manager allows to configure environments for projects with the packages you need.

## Install Conda

## Conda cheatsheet

```
conda --version                             # Get the current version
conda update conda                          # Updates version if available
conda create --name yourname python=2.7     # Creates an environment for a python distribution
conda install PACKAGENAME                   # Installs a package included in Anaconda
source activate ENVIRONMENT                 # Activates environment
source deactivate ENVIRONMENT               # Deactivates environment
```

# Find packages

One of the best things of Pyhton is the huge free software community it has. There is a package for everything in Python. You must learn to search for packages and test them. A good way is to use the [Awesome Python](https://github.com/vinta/awesome-python) github repo that contains a list of well-known packages organised by topics.

# Using C APIs

To use C libraries, [take a look](https://docs.python.org/3.6/extending/extending.html)

# Unit testing

* [Understanding Unit Testing](https://jeffknupp.com/blog/2013/12/09/improve-your-python-understanding-unit-testing/)
* [Unit test python guide](http://docs.python-guide.org/en/latest/writing/tests/)
* [Unit test reference](https://docs.python.org/3/library/unittest.html)

# Resources

* [Virtual environment](https://itsfoss.com/python-setup-linux/)
