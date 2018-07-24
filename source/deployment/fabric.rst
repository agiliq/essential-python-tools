Fabric
----------

`Fabric <http://www.fabfile.org/>`_ is a high level Python (2.7, 3.4+) library designed to execute shell commands remotely over SSH for application deployment.

It provides a basic suite of operations for executing local or remote shell commands (normally or via sudo) and uploading/downloading files, as well as auxiliary functionality such as prompting the running user for input, or aborting execution.

    We can execute shell commands over SSH, so we only need to have SSH running on
    the remote machine. It interact with the remote machines that we specify as if
    they were local. 

**Fabric can be used for many things, including deploying, restarting servers,
stopping and restarting processes.** 


To install fabric :code:`pip install fabric`

Fabric, provides a command line utility, :code:`fab` which looks for a fabfile.py, which is a file containing Python code. 
example fabfile:

.. code-block:: python

    from fabric.api import run
    def diskspace():
        run('df')


The above example provides a function to check free disk space,  :code:`run` command executes a remote command on all specific hosts, with user-level permissions.

The fabfile should be in the same directory where we run the Fabric tool. 
We write all our functions, roles, configurations, etc in a fabfile.

.. and host type, as well as defining a group of hosts on which to run
