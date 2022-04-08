.. include:: global_directives.inc


.. _`script-install`:

**********************
Automated installation
**********************

.. note::

    This feature is still considered *experimental* but greatly simplifies the
    installation of an HRM website compared to the :ref:`manual_install` instructions.
    After a final cycle of testing, this method will become the new
    recommended way to install HRM.

Get the installation script
===========================

|github| To get the latest release directly from our git repository, run the following in a shell:

.. code:: bash

    $ git clone https://github.com/aarpon/hrm_installer

Basic operation
===============

The most basic way to run the script to install HRM is to simply launch `setup.sh` as a priviledge user. In a shell, type the following:

.. code:: bash

    $ sudo ./setup.sh

There are a few prerequisites to take care of before the script is run. In case these are not met, the script will display helpful error messages and abort. You will need:

* A supported OS. For this release, this means Ubuntu 20.04, Debian 11, Rocky Linux 8.5 or AlmaLinux 8.4 only.
* The script must be run as a priviledged user, either as root or using `sudo`.
* You will need an active Internet connection to clone the HRM repository.
* Hucore must be installed and a license available. 

Further documentation
=====================

For now, the documentation is available on https://github.com/aarpon/hrm_installer and better instructions will be added here later.

Getting help
============

If you are interested in this installation method and have any issues you want to discuss, please enquire on the image.sc forum over at https://forum.image.sc/tag/svi-huygens

