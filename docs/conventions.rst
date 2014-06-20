.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

***********
Conventions
***********

This page lists some conventions and notations used in this documentation.

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

|note| Support for |macosx| Mac OS X was dropped in HRM version 3.1.

Variables
=========

+--------------+----------------------------------------+----------------------------------------------+
| Variable     | Description                            | (Example) value                              |
+==============+========================================+==============================================+
| $ROOT        | Web server document root               | /var/www/html                                |
+--------------+----------------------------------------+----------------------------------------------+
| $HRM_ROOT    | HRM root folder                        | $ROOT/hrm                                    |
+--------------+----------------------------------------+----------------------------------------------+
| $CONFIG      | HRM configuration folder               | $HRM_ROOT/config                             |
+--------------+----------------------------------------+----------------------------------------------+
| $RESOURCES   | HRM resources folder                   | $HRM_ROOT/resources                          |
+--------------+----------------------------------------+----------------------------------------------+
| $SETUP       | HRM setup folder                       | $HRM_ROOT/setup                              |
+--------------+----------------------------------------+----------------------------------------------+

|note| Please notice that $ROOT is ``/var/www/html`` in |fedora| as it is in |ubuntu| as of version 14.04 LTS. In earlier versions of |ubuntu|, however, $ROOT used to be ``/var/www``. 
