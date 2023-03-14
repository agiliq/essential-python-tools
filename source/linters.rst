Linters and formatters
-----------------------

PEP8
+++++
`PEP8 <https://www.python.org/dev/peps/pep-0008/?>`_ is the official style guide for python. It is important to know the style-guide if you want to be a part of the python-community.

..  as the code will be easier to read, understand & share.

.. It contains the style conventions which are considered standard in python.

PEP8 coding conventions are:
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


pycodestyle
++++++++++++++++        
`Pycodestyle <https://github.com/PyCQA/pycodestyle>`_ (Formerly PEP8) is the official linter tool to check the python code against the style conventions of PEP8 python. 

To install it:
:code:`pip install pycodestyle`.

Let us take a small example script to test `pycodestyle`

We will create a test script file :code:`test_script.py` and use it as an example for all the linters.

.. code-block:: python

    from __future__ import print_function
    import os, sys
    import logging
    from .. import views

    class DoSomething(SomeCommand) :

        def __init__(self):
            for i in range(1,11):
                if self.number == i:
                    print("matched")
                else:
                    print('not matched')  

        def check_user(self):    
            if self.user: return True   
            else  : return False   


If we run pycodestyle:
:code:`$ pycodestyle {source_file_or_directory}`

.. code-block:: shell

    $ pycodestyle test_script.py 
    test_script.py:2:10: E401 multiple imports on one line
    test_script.py:6:1: E302 expected 2 blank lines, found 1
    test_script.py:6:31: E203 whitespace before ':'
    test_script.py:9:25: E231 missing whitespace after ','
    test_script.py:13:37: W291 trailing whitespace
    test_script.py:16:21: E701 multiple statements on one line (colon)
    test_script.py:16:34: W291 trailing whitespace
    test_script.py:17:13: E271 multiple spaces after keyword
    test_script.py:17:14: E203 whitespace before ':'
    test_script.py:17:15: E701 multiple statements on one line (colon)
    test_script.py:17:29: W291 trailing whitespace


To see the summary, use :code:`--statistics -qq`
:code:`$ pycodestyle --statistics -qq {source_file_or_directory}`



.. code-block:: shell

    $ pycodestyle --statistics -qq test_script.py 
        2       E203 whitespace before ':'
        1       E231 missing whitespace after ','
        1       E271 multiple spaces after keyword
        1       E302 expected 2 blank lines, found 1
        1       E401 multiple imports on one line
        2       E701 multiple statements on one line (colon)
        3       W291 trailing whitespace


We can also make pycodestyle show the error and the description of how to solve the error by using :code:`--show-source --show-pep8`
    
:code:`$ pycodestyle --show-source --show-pep8 {source_file_or_directory}`

.. code-block:: shell

    $ pycodestyle --show-source --show-pep8  test_script.py 
    test_script.py:2:10: E401 multiple imports on one line
    import os, sys
            ^
        Place imports on separate lines.
        ...
        ...
        ...

To customise `pycodestyle` we can configure it at the project-level or in user-level.
It is better to configure at the project level as the style usually varies for every-project.

To **configure** a project's pycodestyle create a :code:`tox.ini` Or a :code:`setup.cfg`

And add 

.. code-block:: shell

        [pycodestyle]
        ignore = E501, W291
        max-line-length = 88
        statistics = True

In the above file , 
    + :code:`[pycodestyle]` tells this is the pycodestyle section
    + we are telling to ignore the Error E501 (which is a line-length error) and Warning W291 (trailing whitespace warning).
    + mentioning the max-line-length to be 88.
    + and to show the statistics with every check


.. list-table:: **PEP8 Error/Warning code**
   :header-rows: 1

   * - Error/ Warning
     - Meaning
   * - Starting with E...
     - Errors
   * - Starting with W...
     - Warnings
   * - 100 type … 
     - Indentation
   * - 200 type … 
     - Whitespace
   * - 300 type … 
     - Blank lines
   * - 400 type … 
     - Imports
   * - 500 type … 
     - Line length
   * - 600 type … 
     - Deprecation
   * - 700 type … 
     - Statements
   * - 900 type … 
     - Syntax errors


.. flake*
.. ++++++++

pylint
++++++++

`Pylint <https://www.pylint.org/>`_ is a python linter which checks the source code and also acts as a bug and quality checker. It has more verification checks and options than just PEP8(Python style guide).

This is the most commonly used tool for linting in python.

It includes the following features:
    + Checking the length of each line
    + Checking if variable names are well-formed according to the project's coding standard
    + Checking if declared interfaces are truly implemented.

To install it:
:code:`pip install pylint`.


Usage:
:code:`pylint {source_file_or_directory}`

Using the file `test_script.py` as an example

.. code-block:: shell


    $ pylint test_script.py 
    No config file found, using default configuration
    ************* Module test_script
    C:  6, 0: No space allowed before :
    class DoSomething(SomeCommand) :
                                ^ (bad-whitespace)
    C:  9, 0: Exactly one space required after comma
            for i in range(1,11):
                            ^ (bad-whitespace)
    C: 13, 0: Trailing whitespace (trailing-whitespace)
    C: 16, 0: Trailing whitespace (trailing-whitespace)
    C: 17, 0: Final newline missing (missing-final-newline)
    C: 17, 0: No space allowed before :
            else  : return False   
                ^ (bad-whitespace)
    C:  1, 0: Missing module docstring (missing-docstring)
    C:  2, 0: Multiple imports on one line (os, sys) (multiple-imports)
    E:  4, 0: Attempted relative import beyond top-level package (relative-beyond-top-level)
    C:  6, 0: Missing class docstring (missing-docstring)
    E:  6,18: Undefined variable 'SomeCommand' (undefined-variable)
    C: 15, 4: Missing method docstring (missing-docstring)
    R: 16, 8: The if statement can be replaced with 'return bool(test)' (simplifiable-if-statement)
    R: 16, 8: Unnecessary "else" after "return" (no-else-return)
    C: 16,22: More than one statement on a single line (multiple-statements)
    R:  6, 0: Too few public methods (1/2) (too-few-public-methods)
    W:  2, 0: Unused import sys (unused-import)
    W:  2, 0: Unused import os (unused-import)
    W:  3, 0: Unused import logging (unused-import)
    W:  4, 0: Unused import views (unused-import)

    ----------------------------------------------------------------------
    Your code has been rated at -10.00/10 (previous run: -10.00/10, +0.00)

As we can see `pylint` has more error/warning checks and options than pep8. And it is more descriptive.


**To customise** `pylint` we can configure it at the project-level, user-level or global-level .

+ create a :code:`/etc/pylintrc` for default global configuration
+ create a :code:`~/pylintrc` for default user configuration
+ Or create a :code:`pylintrc` file   


To create a pylintrc file :code:`pylint --generate-rcfile > pylintrc` , which creates a template pylintrc(with comments) which can be customised as required.

For example if we want the max line lenght to be 88, then we have to set the :code:`max-line-length` to 88  .



pyflakes
+++++++++

`pyflakes <https://pypi.org/project/pyflakes/>`_ is a verification tool(linter) which checks for Python files for errors.
Pyflakes doesn’t verify the style at all but it verifies only logistic errors like the syntax tree of each file individually.

To install it:
:code:`pip install pyflakes`.

Let us take the same example script to test `pyflakes`

Usage:
:code:`pyflakes {source_file_or_directory}`

Using the file `test_script.py` as an example


.. code-block:: shell

    $ pyflakes test_script.py 
    test_script.py:2: 'sys' imported but unused
    test_script.py:2: 'os' imported but unused
    test_script.py:3: 'logging' imported but unused
    test_script.py:4: '..views' imported but unused
    test_script.py:6: undefined name 'SomeCommand'


It detected newly “library imported but unused” and “Undefined name”, it doesn’t verify the style but verify only logistic error.

If we like Pyflakes but also want stylistic checks, we can use flake8, which combines Pyflakes with style checks against PEP 8 


flake8
+++++++++

`Flake8 <http://flake8.pycqa.org/en/latest/>`_ is just a wrapper around `pyflakes`, `pycodestyle` and `McCabe script (circular complexity checker) <https://github.com/PyCQA/mccabe>`_ (which is used to detect complex-code).

If we like Pyflakes but also want stylistic checks, we can use flake8, which combines Pyflakes with style checks against PEP 8 

.. and it can also be configured per project.

To install it:
:code:`pip install flake8`.

Usage:
:code:`flake8 {source_file_or_directory}`

To get statics also
:code:`flake8 {source_file_or_directory} --statistics`

Using the file `test_script.py` as an example


.. code-block:: shell

    $ flake8 test_script.py --statistics
    test_script.py:2:1: F401 'os' imported but unused
    test_script.py:2:1: F401 'sys' imported but unused
    test_script.py:2:10: E401 multiple imports on one line
    test_script.py:3:1: F401 'logging' imported but unused
    test_script.py:4:1: F401 '..views' imported but unused
    test_script.py:6:1: E302 expected 2 blank lines, found 1
    test_script.py:6:19: F821 undefined name 'SomeCommand'
    test_script.py:6:31: E203 whitespace before ':'
    test_script.py:9:25: E231 missing whitespace after ','test_script.py:13:37: W291 trailing whitespace
    test_script.py:16:21: E701 multiple statements on one line (colon)
    test_script.py:16:34: W291 trailing whitespace
    test_script.py:17:13: E271 multiple spaces after keyword
    test_script.py:17:14: E203 whitespace before ':'
    test_script.py:17:15: E701 multiple statements on one line (colon)test_script.py:17:29: W291 trailing whitespace
    2     E203 whitespace before ':'
    1     E231 missing whitespace after ','
    1     E271 multiple spaces after keyword
    1     E302 expected 2 blank lines, found 1
    1     E401 multiple imports on one line
    2     E701 multiple statements on one line (colon)
    4     F401 'os' imported but unused
    1     F821 undefined name 'SomeCommand'
    3     W291 trailing whitespace


The output is formatted as:

.. code-block:: shell

        file path : line number : column number : error code : short description


By adding the :code:`--show-source` option, it'll be easier to find out what parts of the source code need to be revised.

.. code-block:: shell

    $ flake8 test_script.py  --show-source
    test_script.py:2:1: F401 'os' imported but unused
    import os, sys
    ^
    test_script.py:2:1: F401 'sys' imported but unused
    import os, sys
    ^
    test_script.py:2:10: E401 multiple imports on one line
    import os, sys
            ^
    test_script.py:3:1: F401 'logging' imported but unused
    import logging
    ^
    ...
    ...
    ...


We can see the result of pep8 (error code is Exxx and Wxxx) and pyflakes (error code is Fxxx) are output together.

.. We can configure the pyflakes (Fxxx) error by ignore.

Flake8 Error code meaning

The error code of flake8 are :

+ E***/W***:  Errors and warnings of pep8
+ F***:  Detections of PyFlakes
+ C9**:  Detections of circulate complexity by McCabe-script


Flake8 can be customised/configured in :

+ Toplevel User directory, in :code:`~/.config/flake8`  Or
+ In a project folder by one of :code:`setup.cfg`, :code:`tox.ini`, or :code:`.flake8`. 


To customize flake8

.. code-block:: shell

    [flake8]
    ignore = D203
    exclude = .git,__pycache__,docs/source/conf.py,old,build,dist, *migrations*
    max-complexity = 10

This is same as the below one line command

.. code-block:: shell 

    $ flake8 --ignore D203 \
         --exclude .git,__pycache__,docs/source/conf.py,old,build,dist \
         --max-complexity 10




------------

black
++++++

`black <https://black.readthedocs.io/en/stable/>`_  is a python code auto-formatter. 
Black reformats entire files in place and also formats the strings to have double-quotes.

`Black` is not configurable(except for line-length).

To install it:
:code:`pip install black`.

Usage:
:code:`black {source_file_or_directory}`

The response we got when we did :code:`black test_script.py` is

.. image:: _static/black-formatter.png

Using the file `test_script.py` as an example

And the formatted code is


.. code-block:: python

    from __future__ import print_function
    import os, sys
    import logging
    from .. import views


    class DoSomething(SomeCommand):
        def __init__(self):
            for i in range(1, 11):
                if self.number == i:
                    print("matched")
                else:
                    print("not matched")

        def check_user(self):
            if self.user:
                return True
            else:
                return False

To customise  `black`  we have to add this section in :code:`pyproject.toml`


.. code-block:: shell

            [tool.black]
            line-length = 90
            py36 = true
            include = '\.pyi?$'
            exclude = '''
            /(
                \.git
            | \.mypy_cache
            | \.tox
            | \.venv
            | _build
            | buck-out
            | build
            | dist
            )/
            '''

In the above section, we have modified the line-lenght to 90, 
and specified the python version to 3.6



autopep8
+++++++++
`autopep8 <https://pypi.org/project/autopep8/>`_ automatically formats Python code to the PEP8 style. It fixes most of the formatting issues that are reported by pycodestyle.

.. To customise autopep8 check out `autopep8 <https://pypi.org/project/autopep8/#more-advanced-usage>`_ .


To install it:
:code:`pip install autopep8`




Usage(to format a file):
:code:`autopep8 --in-place {file_name}`

here :code:`--in-place` is to make changes to files in place.


Using the file `test_script.py` as an example

This is the formatted code.


.. code-block:: python
    
    from __future__ import print_function
    import os
    import sys
    import logging
    from .. import views


    class DoSomething(SomeCommand):

        def __init__(self):
            for i in range(1, 11):
                if self.number == i:
                    print("matched")
                else:
                    print('not matched')

        def check_user(self):
            if self.user:
                return True
            else:
                return False


.. By default autopep8 only makes whitespace changes and it does not fix statement errors to enable this we have to add :code:`--aggressive` which increases the aggressiveness of formatting the code. By using `--aggressive` we can also fix the statement errors. 

To configure `autopep8` we have to add this section :code:`[pep8]` in :code:`setup.cfg`  :

.. code-block:: shell

    [pep8]
    ignore = E226,E302,E41
    max-line-length = 160





yapf
+++++++++
`Yet another Python formatter <https://github.com/google/yapf>`_ is another auto-formatter which is maintained by google.
`yapf` is highly configurable and it has different base configurations, like pep8, Google and Facebook.



To install it:
:code:`pip install yapf`


Usage:
:code:`yapf -i {source_file_or_directory}`

here :code:`-i` is to make changes to files in place.

This is the formatted code.

.. code-block:: python

    from __future__ import print_function
    import os, sys
    import logging
    from .. import views


    class DoSomething(SomeCommand):
        def __init__(self):
            for i in range(1, 11):
                if self.number == i:
                    print("matched")
                else:
                    print('not matched')

        def check_user(self):
            if self.user: return True
            else: return False


To configure `yapf` we have to add this section :code:`[yapf]` in :code:`setup.cfg`  :

.. code-block:: shell

    [yapf]
    ignore = E226,E302
    max-line-length = 96






------------

Conclusion
+++++++++++++++++ 
Linting:

    `Pylint` and flake8 have the most detailed way of showing the error and warnings(and it also gives the code rating).

.. Formatter:
    
..    `Black` and `yapf` are the most popular ones, while black is still in beta.
