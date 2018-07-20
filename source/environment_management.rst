Environment Management
-----------------------

virtualenv and virtualenvwrapper
++++++++++++++++++++++++++++++++++++++++

virtualenv
=========

`virtualenv <https://virtualenv.pypa.io/en/stable/>`_ is a popular tool for creating isolated python environments without affecting other projects.  

It is really helpful if you are having more than one project at a time, so that there won't be any version clashes among the packages of the projects. 
Example , if you want to work with more python2.7 for one project and python3.5 for another project, virtualenv solves the purpose.

It creates an environment that has its own isolated installation directories, that doesn’t share libraries with other virtualenv environments.


We have to install it globally:
:code:`[sudo] pip install virtualenv` 

Once we have virtualenv installed, we have to create the a directory for our virtualenv 
:code:`mkdir ~/virtualenvironment`


virtualenvwrapper
=========

`virtualenvwrapper <http://virtualenvwrapper.readthedocs.io/en/latest/>`_ is an just like an extension to `virtualenv` which simplifies the commands to use and manage. 


To install it:
    :code:`[sudo] pip install virtualenvwrapper`

After installing, Add these lines to your shell startup file (:code:`.bashrc`, :code:`.profile`, etc.) 

.. code-block:: shell

    export WORKON_HOME=$HOME/.virtualenvs
    export PROJECT_HOME=$HOME/Devel
    source /usr/local/bin/virtualenvwrapper.sh


After editing the file, reload the startup file (e.g., run :code:`source ~/.bashrc`).

We tell the startup file to set the location where the virtual environments should live, the location of your development project directories, and the location of the script installed with this package:

Next, we can create the virtualenv with command :code:`mkvirtualenv`
This command creates the virtualenv and automatically loads it for us.

.. code-block:: shell
    
    $ mkvirtualenv testEnv
    New python executable in /Users/anmol/.virtualenvs/testEnv/bin/python2.7
    Also creating executable in /Users/anmol/.virtualenvs/testEnv/bin/python
    Installing setuptools, pip, wheel...done.
    virtualenvwrapper.user_scripts creating /Users/anmol/.virtualenvs/testEnv/bin/predeactivate
    virtualenvwrapper.user_scripts creating /Users/anmol/.virtualenvs/testEnv/bin/postdeactivate
    virtualenvwrapper.user_scripts creating /Users/anmol/.virtualenvs/testEnv/bin/preactivate
    virtualenvwrapper.user_scripts creating /Users/anmol/.virtualenvs/testEnv/bin/postactivate
    virtualenvwrapper.user_scripts creating /Users/anmol/.virtualenvs/testEnv/bin/get_env_details
    (testEnv) $ 

To come out of the virtualenv use command :code:`$ deactivate`

If you want to create a virtualenv with a different version of python like python3(which should be globally installed) then specify the python version using :code:`-p python3`

.. To create the virtualenv with different version of python, use this command :code:`$ mkvirtualenv testEnv -p python3`

My system created the virtualenv with my default python which is python2.7.
If you also have python3 installed in your system and you want to create the virtualenv with python3 then create the virtualenv with this command :code:`mkvirtualenv testEnv -p python3`

.. code-block:: shell

    $ mkvirtualenv testEnv -p python3
    Running virtualenv with interpreter /usr/local/bin/python3
    Using base prefix '/usr/local/Cellar/python3/3.6.4_2/Frameworks/Python.framework/Versions/3.6'
    New python executable in /Users/anmol/.virtualenvs/testEnv/bin/python3
    Installing setuptools, pip, wheel...done.
    (testEnv) $ python -V
    Python 3.6.4
    (testEnv) $



To list all virtualenvs present in the system run command: :code:`$ workon`
`workon` lists all the virtualenvs present in the system.

To start working in a virtualenv:   :code:`$ workon <name_of_virtualenv>`

To remove/delete a virtualenv:      :code:`$ rmvirtualenv <name_of_virtualenv>`



pipenv
++++++++

`Pipenv <https://docs.pipenv.org/>`_ is a tool for creating a separate/isolated working environment which manages the dependency versions. It creates virtualenv for every project in the project folder.


To install it:
    :code:`[sudo] pip install pipenv`

Next, to create a pipenv for a project, go to the project directory and type

.. code-block:: shell

    $ pipenv install <package>   // like pipenv install requests 
    
.. code-block:: shell

    $ pipenv install -r requirements.txt   // if our dependencies are listed in a file
    
    $ pipenv --python python3 install  <package>  // with different version of python like python3

after creating a pipenv, 2 files will be created **Pipfile** and **Pipfile.lock** which lists all our packages and these files get updated whenever we install/update/delete any package.

If we want to add a package for only development/testing then use :code:`pipenv install -d `


To activate this project's virtualenv, run  :code:`pipenv shell`

And to run a command inside the virtualenv with :code:`pipenv run` . example :code:`pipenv run python hello.py`

And to exit the virtualenv run :code:`exit`



pip, requirement.txt and pipfile
++++++++++++++++++++++++++++++++++++++++
`Pip <https://pip.pypa.io/en/stable/>`_(Python's package manager) is a package management system used to install and manage software packages written in Python. 

To check pip version:
    :code:`pip -V`


To get pip:
    :code:`python get-pip.py`

List all packages installed :
    :code:`pip freeze`   

To install/unistall a package using pip:

.. code-block:: shell

    pip install <pacakge>   // install
    pip install <pacakge>==1.2.2   // install a specific version
    pip uninstall <pacakge>   // uninstall


**Requirement.txt**   is a text file which stores the list of all the pip packages with versions which are required to run the project.

To create a `requirements.txt` file do :code:`pip freeze > requirements.txt`

A sample requirements.txt file 

.. code-block:: shell

    Django==2.0.3
    djangorestframework==3.7.7
    django-rest-swagger==2.1.2
    coreapi==2.3.3


**Pipfile**  is just a replacement to the requirement.txt file. pipfile is generated when using `pipenv`.

    Pipfile lists all the packages by separating the development/testing packages from the main packages used and also mentions the python version it uses.


A sample Pipfile

.. code-block:: shell

        [[source]] 
        url = "https://pypi.python.org/simple"
        verify_ssl = true
        name = "pypi"

        [packages] 
        coverage = "*"
        requests = "*"

        [dev-packages] 
        pylint = "*"

        [requires] 
        python_version = "3.6"


poetry
++++++++
`Poetry <https://poetry.eustace.io/>`_ is a tool for dependency management and packaging in Python. It allows us to declare the libraries your project depends on and it will manage (install/update) them for us.

Poetry can be installed using pip, but the recommended way to install is 

:code:`curl -sSL https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py | python` 

To use poetry run this command:
:code:`poetry init`

This command will help you create a :code:`pyproject.toml` file interactively by prompting you to provide basic information about your package. 

**pyproject.toml** is the main file which manages all the dependencies.

    `pyproject.toml <https://poetry.eustace.io/docs/pyproject/>`_ file contains all the details of the project. It mentions the dependencies/dev-dependencies and also other details like name, description, author, version etc  of project.

A sample `pyproject.toml`

.. code-block:: shell

        [tool.poetry]
        name = "base-ing"
        version = "0.1.0"
        description = ""
        authors = ["anmol <anmol@agiliq.com>"]

        [tool.poetry.dependencies]
        python = "*"

        [tool.poetry.dev-dependencies]


To add/remove a package :
:code:`poetry add <package>`
:code:`poetry remove <package>`


To add a package as a development-dependency:
:code:`poetry add <package> --dev`


To run a command in poetry 
:code:`poetry run python hello.py`


A comparision of the tools
++++++++++++++++++++++++++++++++++++++++

Python/pip Standard
===========================
Both pipenv and virtualenvwrapper are officially recommended and are considered as standards.

Easy of use.
==================
Pipenv and virtualenvwrapper both are easy to use. 
.. Poetry is 



For beginners I suggest, start with `virtualenv/virtualenvwrapper` and then use `pipenv` .   









