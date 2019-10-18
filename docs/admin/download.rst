.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. _`download-hrm`:


***********
Get the HRM
***********

Current version
===============

Current version of the HRM is |HRM_VERSION|.

.. _download-hrm-standard:

Download archive
================

Download the latest version of HRM, unpack the code and install it following the :ref:`manual_install` instructions.

|linux| `Download the archive <https://sourceforge.net/projects/hrm/files/latest/download>`_.

.. note::

	We are working on installation scripts to automate the process!

Clone git repository
====================

|github| To get the **latest stable** release directly from our git repository, run the following in a shell:

.. code:: bash

    $ git clone -b master --single-branch https://github.com/aarpon/hrm
    $ cd hrm
    $ ./setup/setup_release.sh


|github| If you want to follow the HRM development, you can checkout the read-only HRM repository and
and configure your working copy for development.

.. code:: bash

    $ git clone https://github.com/aarpon/hrm
    $ cd hrm
    $ git checkout devel
    $ ./setup/setup_devel.sh

Find more detailed instructions in the  :ref:`installation pages<install-hrm-git>`.

.. warning::

    Please keep in mind that the latest development snapshot is **unstable software and should not be deployed on production machines!**
