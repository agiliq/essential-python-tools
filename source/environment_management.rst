Environment Management
-----------------------

virtualenv and virtualenvwrapper
++++++++++++++++++++++++++++++++++++++++

.. virtualenv
.. =========

`virtualenv <https://virtualenv.pypa.io/en/stable/>`_ is a tool for creating isolated python environments without affecting other projects.  

It is really helpful if you are having more than one project at a time, so that there won't be any version clashes among the packages of the projects.

It creates an environment that has its own installation directories, that doesn’t share libraries with other virtualenv environments.

`virtualenvwrapper <http://virtualenvwrapper.readthedocs.io/en/latest/>`_ is an just like an extension to `virtualenv` which simplifies the commands to manage the virtualenv. 

pipenv
++++++++

`Pipenv <https://docs.pipenv.org/>`_ is a tool for creating a separate/isolated working environment which manges the dependency versions.


pip, requirement.txt and pipfile
++++++++++++++++++++++++++++++++++++++++
`pip <https://pip.pypa.io/en/stable/>`_ is a package management system used to install and manage software packages written in Python.

`requirement.txt`   is a text file which stores the list of all the pip packages with versions which are required to run the project.

`pipfile`  is just a replacement to the requirement.txt file. pipfile is generated when using `pipenv`.

poetry
++++++++
`Poetry <https://poetry.eustace.io/>`_ is a tool for dependency management and packaging in Python. It allows us to declare the libraries your project depends on and it will manage (install/update) them for us.

Poetry can be installed using pip, but the recommended way to install is 

:code:`curl -sSL https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py | python` 

A comparision of the tools
++++++++++++++++++++++++++++++++++++++++
