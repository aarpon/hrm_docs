.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. _conventions:

***********
Conventions
***********

This page lists some conventions and notations used in this documentation.

Using ``sudo``
==============

Throughout this document, we're assuming that commands which require root
permissions can be issued by using ``sudo``. If your system is not configured
for this, you can either login directly as ``root`` (considered as "bad
practice") or use the ``su -`` command to switch to the root user.

|note| We highly recommend the usage of ``sudo`` though!


.. _conventions-os:

Operating systems
=================

The recommended linux distributions are:

+--------------+----------------------------------------+
| Icon         | Distribution name                      |
+==============+========================================+
| |debian|     | Debian                                 |
+--------------+----------------------------------------+
| |ubuntu|     | Ubuntu                                 |
+--------------+----------------------------------------+
| |centos|     | CentOS                                 |
+--------------+----------------------------------------+
| |fedora|     | Fedora (not tested for HRM ver. > 3.5) |
+--------------+----------------------------------------+

We will use tabs to group the code and instructions for respective operating system families

+--------------+----------------------------------------+
| Tab name     | Corresponding operating system family  |
+==============+========================================+
| Debian       | Debian, Ubuntu                         |
+--------------+----------------------------------------+
| RHEL         | Fedora, CentOS                         |
+--------------+----------------------------------------+

.. warning::

    Please notice that with release 3.1, we dropped support for |macosx| **Mac OS X**. HRM 3.0 is still known to work on Mac OS X from 10.5 (Leopard) onward, but no effort will be made to make future versions of the HRM compatible with Mac OS X. Also notice that the HRM was never tested on Mavericks.

Variables
=========

+--------------+----------------------------------------+----------------------------------------------+
| Variable     | Description                            | (Example) value                              |
+==============+========================================+==============================================+
| $WWW_ROOT    | Web server document root               | /var/www/html                                |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_HOME    | HRM root (home) folder                 | $WWW_ROOT/hrm                                |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_CONFIG  | HRM configuration folder               | $HRM_HOME/config                             |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_SAMPLES | HRM configuration samples folder       | $HRM_HOME/config/samples                     |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_RESRC   | HRM resources folder                   | $HRM_HOME/resources                          |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_SETUP   | HRM setup folder                       | $HRM_HOME/setup                              |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_BIN     | HRM executables folder                 | $HRM_HOME/bin                                |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_USER    | HRM customization folder               | $HRM_HOME/user                               |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_LOG     | HRM logging folder                     | /var/log/hrm                                 |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_DATA    | HRM data folder                        | /data/hrm_data                               |
+--------------+----------------------------------------+----------------------------------------------+

If you want to use those variables in your interactive shell later on, just
copy-paste the following lines into your session and adjust the values
accordingly:

.. code-block:: sh

    WWW_ROOT=/var/www/html                 # Web server document root
    HRM_HOME=$WWW_ROOT/hrm                 # HRM root (home) folder
    HRM_CONFIG=$HRM_HOME/config            # HRM configuration folder
    HRM_SAMPLES=$HRM_HOME/config/samples   # HRM configuration samples folder
    HRM_RESRC=$HRM_HOME/resources          # HRM resources folder
    HRM_SETUP=$HRM_HOME/setup              # HRM setup folder
    HRM_BIN=$HRM_HOME/bin                  # HRM executables folder
    HRM_USER=$HRM_HOME/user                # HRM customization folder
    HRM_LOG=/var/log/hrm                   # HRM logging folder
    HRM_DATA=/data/hrm_data                # HRM data folder
