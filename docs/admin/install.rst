.. _`install-hrm`:

.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

***************
Install the HRM
***************

... From an Archive
===================

Download or checkout the HRM as explained in :ref:`getting the HRM <download-hrm>`.

Unpack the downloaded archive to web server document root directory. This is the
directory where Apache2 finds the html and php files to serve.

.. code-block:: sh

    sudo unzip hrm_x.y.z.zip -d /var/www/html

where ``x.y.z`` is a placeholder for the HRM version.

.. note::

    You can of course extract or clone the HRM somewhere else: just add the location to the Apache2 configuration (``httpd.conf``).


.. _`install-hrm-git`:

... Using Git
=============

The advantage of using git is that later :ref:`upgrades <upgrade-hrm>` are easy to perform, and all the modifications are documented this way.
You need to install git on the machine.

.. tabs::
    .. tab:: Debian

        .. code-block:: sh

            sudo apt install git

    .. tab:: RHEL

        .. code-block:: sh

            sudo yum install git

Then you can change directory to the hrm document root and check out the git repository.

.. code-block:: sh

    cd $WWW_ROOT
    git clone https://github.com/aarpon/hrm.git
    cd hrm
    git tag -l

In this project tags are used to mark the different version in the master branch. the last command (see above) gives you a list of all the
available versions of the HRM. Usually you can checkout the highest version numbers, except if there are certain compatibility issues.

.. code-block:: sh

    git checkout <tag>

Once the latest release is checked out, you might want to create a local branch before starting to configure the HRM.
Per default the ``$HRM_HOME/config`` is in the ``.gitignore`` file, so if you want to put your configurations under version control you have to modify the ``.gitignore`` first.

.. code-block:: sh

    git checkout -b deployed (optional)