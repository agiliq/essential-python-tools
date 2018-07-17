Liters and formatters
-----------------------

pep8
+++++
`pep8 <https://www.python.org/dev/peps/pep-0008/?>`_ is the official style guide for python.

pep8 coding conventions are:
    + Spaces are the preferred indentation method.
    + Use 4 spaces per indentation level.
    + Limit all lines to a maximum of 79 characters.
    + Separate top-level function and class definitions with two blank lines.
    + Method definitions inside a class are surrounded by a single blank line.
    + Imports should be grouped in the following order:
        + Standard library imports.
        + Related third party imports.
        + Local application/library specific imports.
        + A blank line between each group of imports.



pylint
++++++++

`Pylint <https://www.pylint.org/>`_ is a source code, bug and quality checker for the Python. It follows the style recommended by PEP8, the Python style guide.

This is the most commonly used tool for linting in python.

It includes the following features:
    + Checking the length of each line
    + Checking if variable names are well-formed according to the project's coding standard
    + Checking if declared interfaces are truly implemented.

To install it:
:code:`pip install pylint`.




pyflakes
+++++++++

`pyflakes <https://pypi.org/project/pyflakes/>`_ is a program which checks for Python files for errors.
Pyflakes only examines the syntax tree of each file individually.

To install it:
:code:`pip install pyflakes`.

Usage:
:code:`pyflakes {source_file_or_directory}`

black
++++++

`black <https://black.readthedocs.io/en/stable/>`_  is a python code formatter.

To install it:
:code:`pip install black`.

Usage:
:code:`black {source_file_or_directory}`

autopep8
+++++++++
`autopep8 <https://pypi.org/project/autopep8/>`_ automatically formats Python code to the PEP8 style.



To install it:
:code:`pip install autopep8`
