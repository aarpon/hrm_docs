.. include:: global_directives.inc

.. _get_hrm:

***************
Get the HRM
***************

Current version of the HRM is |HRM_VERSION|.


From archive
===================

Download or checkout the HRM from |linux| `Sourceforge <https://sourceforge.net/projects/hrm/files/latest/download>`_
and unzip it into the ``$WWW_ROOT``.

Bellow is an command example:


.. code-block:: sh

    sudo unzip hrm_3.9.0.zip -d /var/www/html



.. _`install-hrm-git`:

Using Git
=============

The advantage of using git is that later :ref:`upgrades <upgrade-hrm>` are easy to perform, and all the modifications are documented this way.
You need to install git on the machine.

.. tabs::
    .. tab:: Debian

        .. code-block:: sh

            sudo apt install git

    .. tab:: RHEL

        .. code-block:: sh

            sudo dnf install git


|github| To get the **latest stable** release directly from our git repository, change to the ``$WWW_ROOT`` directory and run the following in a shell:

.. code:: bash

    cd $WWW_ROOT
    git clone -b master --single-branch https://github.com/aarpon/hrm
    cd hrm
    ./setup/setup_release.sh


To use an older release, versions can be listed with:

.. code-block:: sh

    git tag -l

The tags are the version numbers, that can be used to work with a specific release by checking it out:

.. code-block:: sh

    git checkout <tag>

Once the release of choice is checked out, you might want to create a local branch before starting to configure the HRM.

.. code-block:: sh

    git checkout -b deployed

Per default the ``$HRM_HOME/config`` is in the ``.gitignore`` file, so if you want to put your configurations under version control you have to modify the ``.gitignore`` and commit your changes to the "deployed" branch.


HRM development
---------------

|github| If you want to follow the **HRM development**, you can checkout the read-only HRM repository and
and configure your working copy for development:

.. code:: bash

    $ git clone https://github.com/aarpon/hrm
    $ cd hrm
    $ git checkout devel
    $ ./setup/setup_devel.sh

Find more detailed instructions in the  :ref:`installation pages<install-hrm-git>`.

.. warning::

    Please keep in mind that the latest development snapshot is **unstable software and should not be deployed on production machines!**
