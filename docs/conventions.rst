.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

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

Operating systems
=================

We will use visual shortcuts to refer to the operating system families supported by the HRM, as in the following table:

+--------------+----------------------------------------+
| Icon         | Corresponding operating system family  |
+==============+========================================+
| |fedora|     | Fedora, CentOS, RHEL                   |
+--------------+----------------------------------------+
| |ubuntu|     | Ubuntu and derivatives                 | 
+--------------+----------------------------------------+

.. warning::

    Support for |macosx| Mac OS X was dropped in HRM version 3.1.

Variables
=========

+--------------+----------------------------------------+----------------------------------------------+
| Variable     | Description                            | (Example) value                              |
+==============+========================================+==============================================+
| $ROOT        | Web server document root               | /var/www/html                                |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_HOME    | HRM root (home) folder                 | $ROOT/hrm                                    |
+--------------+----------------------------------------+----------------------------------------------+
| $CONFIG      | HRM configuration folder               | $HRM_HOME/config                             |
+--------------+----------------------------------------+----------------------------------------------+
| $SAMPLES     | HRM configuration samples folder       | $HRM_HOME/config/samples                     |
+--------------+----------------------------------------+----------------------------------------------+
| $RESOURCES   | HRM resources folder                   | $HRM_HOME/resources                          |
+--------------+----------------------------------------+----------------------------------------------+
| $SETUP       | HRM setup folder                       | $HRM_HOME/setup                              |
+--------------+----------------------------------------+----------------------------------------------+
| $BIN         | HRM executables folder                 | $HRM_HOME/bin                                |
+--------------+----------------------------------------+----------------------------------------------+
| $USER        | HRM customization folder               | $HRM_HOME/user                               |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_DATA    | HRM data folder                        | /data/hrm_data                               |
+--------------+----------------------------------------+----------------------------------------------+

.. note::
    
    Please notice that $ROOT is ``/var/www/html`` in |fedora| and in |ubuntu| as of version 14.04 LTS. In earlier versions of |ubuntu|, however, $ROOT used to be ``/var/www``. 
