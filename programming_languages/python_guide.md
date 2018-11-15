# A guide for Python

If you are a python developer you need to set up your IDE, your environment, know how to search for packages and follow a Python coding convention.

## Choose your IDE

Your python IDE must provide IntellinSense, linting, debugging, a built in console and other tools you consider usefull.

The IDEs I prefer for python are:

- Visual Studio Code
- Pycharm

## Style

It is important to set a **coding convention** or **style guide** before you start developing. Some popular coding conventions are:
- [pep8](https://www.python.org/dev/peps/pep-0008/)
- [Google Style Guide](https://google.github.io/styleguide/pyguide.html)

The style guide must define the way you name projects, classes, functions and variables.

You can use **pylint** for automating rules in style, so you don't have to manually revise the code.

## Virtual environments

Python can be used in a virtual environment like [Conda](https://conda.io/docs/index.html). The package manager allows to configure environments for projects with the packages you need.

### Install Conda

### Conda cheatsheet

`conda --version`                             Get the current version

`conda update conda`                          Updates version if available

`conda create --name yourname python=2.7`     Creates an environment for a python distribution

`conda install PACKAGENAME`                   Installs a package included in Anaconda

`source activate ENVIRONMENT`                 Activates environment

`source deactivate ENVIRONMENT`               Deactivates environment

## Find packages

One of the best things of Pyhton is the huge free software community it has. There is a package for everything in Python. You must learn to search for packages and test them. A good way is to use the [Awesome Python](https://github.com/vinta/awesome-python) github repo that contains a list of well-known packages organised by topics.
