Source code management
+++++++++++++++++++++++++

git
------------
`Git <https://git-scm.com/>`_ is a version control system for tracking changes in computer files or a folder and coordinating work on those files among multiple people.
    
    Git/Version Control System is the basic tool in software development.

.. Version control system is a must for software development.

The main purpose of Git is to manage software development projects and its files, as they are changing over time. It stores the information in a repository.

To install git check `this <https://git-scm.com/book/en/v2/Getting-Started-Installing-Git>`_ . 

To learn git check `this <https://git-scm.com/docs/gittutorial>`_ and `this <https://try.github.io/>`_





github
---------
`GitHub <https://github.com/>`_ is a web-based hosting service for version control using Git. 
It provides access control and several collaboration features such as issue tracking, feature requests, documentation, and wikis for every project.

    With git, we can collaborate with other developers, track all our work via commits, and revert to any previous version of our code even if we accidentally delete something.

GitHub projects can be public or private and every publicly shared code is freely open to everyone. We can have private projects as well, though, they require a paid GitHub plan.
Public repositories on Github are often used to share Open Source Software

It is the most-widely used web-based hosting service, and it has the largest number of open-source projects.




gitlab
-------
`GitLab <https://about.gitlab.com/>`_ is a web-based and self-based hosting service for version control using Git. 
Gitlab is free and open-source. 

Gitlab offers unlimited free public/private repositories, where as Github offers unlimited public repositories only(private repositories require a paid plan)

GitLab offers all the features of Github plus builtin CI/CD service (Continuous Integration & Continuous Delivery), and more authentication levels. 






Countinous Integration
-------------------------
Continuous Integration (CI) is a development practice which automates the build and testing process of the code.
Continuous Integration automates the build and testing processes. The main objective of CI is to test code for every push made to the repository. We need to have a testing framework for the test in CI.

 **Each push is verified by an automated build and tests, individual changes are immediately tested and reported on when they are added to a repository, allowing developers to detect problems early.**

CI encourages developers to integrate their code into a main branch of a shared repository.
Instead of building out features in isolation and integrating them at the end of a development cycle, code is integrated with the shared repository by each developer multiple times throughout the day.

CI makes code integration a simple, fast process that is part of the everyday development workflow in order to reduce integration costs and respond to defects early.

.. To develop, test, and release software in a quick and consistent way, developers and organizations have created three related but distinct strategies to manage and automate these processes.



.. Countinous Delivery
.. -------------------------
.. Countinous Delivery comes after Continuous Integration, it automates the software release and deployment process.


gitlab-ci
=======
`Gitlab Continuous Integration(CI) <https://about.gitlab.com/features/gitlab-ci-cd/>`_ is a open-source CI service that is included in gitlab and can be used for all projects in gitlab. 

To use GitLab CI, you first need to add a :code:`.gitlab-ci.yml` file to the root directory of your repository, as well as configure your GitLab project to use a Runner. Afterwards, every commit or push will trigger the CI pipeline that has three stages: build, test and deploy.

To set up `.gitlab-ci.yml` file follow this `official doc <https://docs.gitlab.com/ee/ci/quick_start/>`_ 


circleci
===========
`Circleci  <https://circleci.com/>`_   is a cloud-based continuous integration server.
It supports containers, OSX, Linux and can run within a private cloud or our own data center.
that supports any language that builds on Linux or macOS.

It is available in both cloud-based and self-hosted.

Setting up CircleCI:
    + Sign-in to circleci.com and link your project.
    + After that activate the service hook to that repo in the profile page of cirlceci .
    + Add circle.yml to the project

To set up `.circle-ci.yml` file follow this `official doc <https://circleci.com/docs/enterprise/quick-start/>`_   and
for python apps  - `config circleci for python apps <https://circleci.com/docs/2.0/language-python/>`_
