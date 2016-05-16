.. _client-testing:

Client Testing
==============

Automated Testing
-----------------

Flocker includes client installation tests and a tool for running them in Docker containers.

The client tests are called like this:

.. prompt:: bash $

   admin/run-client-tests <options>


The :program:`admin/run-client-tests` script has several options:

.. program:: admin/run-client-tests

.. option:: --distribution <distribution>

   Specifies the distribution on which to run the installation test.

.. option:: --branch <branch>

   Specifies the branch repository from which to install packages.
   If this is not specified, packages will be installed from the release repository.

.. option:: --flocker-version <version>

   Specifies the version of Flocker to install from the selected repository.
   If this is not specified, the most recent version available in the repository will be installed.

   .. note::

      The build server merges forward before building packages, except on release branches.
      If you want to run the client tests against a branch in development,
      you probably only want to specify the branch.

.. option:: --build-server <buildserver>

   Specifies the base URL of the build server to install from.
   This is probably only useful when testing changes to the build server.

.. option:: --pip

   Use pip to install the client, rather than using packages.
   The wheel files, used for pip installations, are only generated for releases.
   Hence, for ``pip`` installations, the ``--branch`` value is ignored, and any non-release ``--flocker-version`` value is modified to the previous release.

To see the supported values for each option, run:

.. prompt:: bash $

   admin/run-client-tests --help


Manual Testing
--------------

Sometimes it is useful to manually test CLIs and their installation instructions on various platforms.

OS X
~~~~

In order to test on OS X you must find someone who has a Mac computer and ask them to spin up an OS X Virtual Machine to manually test CLIs and their installation.

Linux
~~~~~

To test on various Linux distributions, it is possible to create a Docker container.

For example, choose a Docker image from the `Docker Hub <https://hub.docker.com/>`_, and run either of the following commands to start it:

.. prompt:: bash $

   docker run -i -t ubuntu /bin/bash

or:

.. prompt:: bash $

   docker run -i -t fedora:20 /bin/bash

This will likely allow you to test commands as a root user.
If you want to test as a non-root user, create a new user which has the ability to use ``sudo``.
