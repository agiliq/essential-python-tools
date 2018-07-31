Docker
-----------

`Docker <https://www.docker.com/what-docker>`_ is an open-source tool for creating, deploying, and running applications by using containers.
 Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package.

By using containers, the application will run on any machine regardless of any customized settings that machine might have that could differ from the machine used for writing and testing the code.

.. its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.

Containerization is an approach in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.

 The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).

Docker is an open-source tool for automating the deployment of applications.



Docker Compose
++++++++++++++++++++
`Compose <https://docs.docker.com/compose/overview/>`_ is a tool for running multi-container applications like for example a container with a DataBase and an application.
We can start/stop multiple services using compose with a single command.

    We can create multiple compose files each for production, staging, development, testing, as well as CI,
    and each will be isolated with each other.

To use compose 

+ Create a :code:`Dockerfile` where all our environment configuration and initial packages are mentioned.
+ Create a file :code:`docker-compose.yml` , and mention all the services which we would be using.
+ Finally run :code:`docker-compose up` . 


:code:`Dockerfile`

.. code-block:: shell

        FROM python:3.4-alpine                      # 1
        ADD . /code             #2
        WORKDIR /code        #3
        ADD requirements.txt /code/         #4
        RUN pip install -r requirements.txt       #5
        
                

In the above file we 

+ In :code:`#1` we are building an image starting with the Python 3.4 image
+ In :code:`#2` and :code:`#3` we are adding directory :code:` . ` into the path :code:`/code` in the image and making it the working directory.
+ In :code:`#4` and :code:`#5` we adding the requirements file to the :code:`/code/` directory and installing all requirements.

.. + In :code:`#6` we are running the command :code:`python app.py`

:code:`docker-compose.yml`

.. code-block:: shell

        version: '3'           # 1

        services:            # 2
            web:
                build: .        # 3
                command: python3 manage.py runserver 0.0.0.0:8000   #4
                volumes:                                    # 5
                - .:/code
                ports:                          #6
                - "8000:8000"
                depends_on:                #7
                - db
            db:
                image: postgres


+ In :code:`#1` we mention the docker version (which is 3)
+ :code:`#2` defines two services, web and db. 

    + The :code:`web` service uses an image that’s built from the Dockerfile 
    + The :code:`db` service uses a public Postgres image pulled from the Docker Hub registry.

+ :code:`#3` tells to find the the dockerfile in the current directory 
+ :code:`#4` is a command to run the service .
+ :code:`#5` tells the host paths for that service.
+ :code:`#6` forwards the exposed port 8000 on the container to port 8000 on the host machine. 
+ :code:`#7`  mentions the dependency between services



To use the docker compose , we use commands

.. code-block:: shell

        $ docker-compose up          # to create and start the containers

        $ docker-compose build        #to build or rebuild services

        $ docker-compose up --build        # build the services and start the containers



.. example of docker for deploying/development/testing for django/flask



**We write different `docker-compose` files for each  Development, Testing, & Production.**


