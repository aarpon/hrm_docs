.. include:: global_directives.inc

*************************
Install the prerequisites
*************************

The HRM requires a few prerequisites for its functions.

Operating system
================

If you have not yet read the conventions, please consult the :ref:`conventions-os`.

.. note::

    For those who plan on using the :ref:`prerequisites-omero` it is strongly
    recommended to set up the HRM and OMERO using the same Linux *distribution*
    and *version*, simply to avoid `Ice <http://www.zeroc.com>`_ version
    incompatibilities, which will prevent the HRM-OMERO connector from working.
    Details can be found in the `OMERO system administrator documentation
    <https://www.openmicroscopy.org/site/support/omero5/sysadmins/index.html>`_.

    PLEASE MIND: this does **NOT** mean you should install HRM and OMERO on the
    **same machine**! You should just run the same Linux installation on them.

Huygens Core
============

The HRM is an interface to Scientific Volume Imaging's `Huygens Core <http://www.svi.nl/HuygensCore>`_. **Huygens Core** is is a fully scriptable compute engine intended to run image processing and deconvolution jobs on large 64 bit multiprocessor servers in headless mode, i.e. without a specific graphical interface. The HRM provides such an interface for multi-user, batch access to Huygens Core.

.. note::

    If the web and the processing server are not on the same machine, you will need an additional Huygens Core for the web server with a **reader license** (free of charge).

Apache2 web server
==================


.. tabs::

   .. code-tab:: bash Debian

      sudo apt install apache2

   .. code-tab:: bash RHEL

      sudo dnf install httpd
      sudo systemctl enable httpd

Web pages can be installed globally or per-user.

The Apache2 global document root is ``/var/www/html``.

If you plan to install the HRM in a specific user directory, use ``/home/<hrm_user>/public_html``.

Apache2 access handling
-----------------------

HRM uses ``.htaccess`` files to prevent access to configuration files.
Make sure to configure Apache2 to use them by setting the *AllowOverride* and *Require* directives in configuration files.

.. tabs::
    .. tab:: Debian

        ``/etc/apache2/sites-available/000-default.conf``

        If you are installing HRM in your user directory also put the directives in
        ``/etc/apache2/mods-available/userdir.conf``
        Make sure to enable the userdir mod first by running the follwing line in the shell:

        .. code-block:: sh

            sudo a2enmod userdir

        See also `Enabling use of Apache htaccess files <https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles>`_.

    .. tab:: RHEL

        ``/etc/httpd/conf.d/hrm.conf`` (the file has to be created)

        If you are installing HRM in your user directory also put the directives in:
        ``/etc/httpd/conf.d/userdir.conf``

        See also `Apache Userdir with SELinux on Fedora 23/22, CentOS/RHEL 7.2/6.7/5.11 <http://www.if-not-true-then-false.com/2010/enable-apache-userdir-with-selinux-on-fedora-centos-red-hat-rhel/>`_.



Please notice that the ``Require`` directive is required from Apache version 2.4. Here is the code snippet for the config
files

.. code-block:: bash

    <Directory /var/www/html/hrm>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>


PHP
===

.. note::

    Minimum required PHP version is **8.1**.

The HRM is made of two parts, a web interface and a queue manager, both written in PHP but with different requirements. The web interface requires the PHP module for Apache2, the queue manager requires the PHP command line interpreter.

.. tabs::

    .. code-tab:: bash Debian

        sudo apt install \
            libapache2-mod-php \
            php \
            php-cli \
            php-common \
            php-json \
            php-xml \
            php-ldap \
            php-mbstring

    .. code-tab:: bash RHEL

        sudo dnf install \
            php \
            php-cli \
            php-common \
            php-process \
            php-json \
            php-xml \
            php-ldap \
            php-mbstring

.. note::

    When installing a PHP version that is not the default of your system it
    might be necessary to specify for which PHP version the packages are
    needed. Change ``php`` to for example ``php8.1`` in the packages to get
    the packages for PHP 8.1. It might also be necessary to change the PHP
    version Apache2 uses with the ``a2dismod`` and ``a2enmod`` commands.
    
   

Production php.ini settings
---------------------------

Please configure the HRM machine for production. Edit the ``php.ini`` configuration file

.. tabs::
    .. tab:: Debian

        ``/etc/php/8.1/apache2/php.ini``

    .. tab:: RHEL

        The corresponding file is ``/etc/php.ini`` but at least as of RHEL 8 all
        default settings are fine, so there shouldn't be anything to change.

In there set at least the values below (more information can be found in the ``php.ini`` file itself).

.. code-block:: bash

    display_errors = Off
    display_startup_errors = Off
    error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT


A relational database
=====================

The HRM officially supports two relational databases: **MySQL** and **PostgreSQL**.


MySQL
-----

.. tabs::

    .. code-tab:: bash Debian

        sudo apt install php-mysql mysql-server

    .. code-tab:: bash RHEL

        sudo dnf install php-mysqlnd php-pdo mariadb-server

        sudo systemctl enable mariadb

.. note::

    It is recommended to install a database management tool like ``phpmyadmin``.


PostgreSQL
----------

.. tabs::
    .. code-tab:: bash Debian

        sudo apt install php-pgsql postgresql

    .. code-tab:: bash RHEL

        sudo dnf install php-pgsql postgresql-server postgresql-contrib

You will need to manually enable PostgreSQL:

.. code-block:: sh

    sudo systemctl enable postgresql

.. note::

    It is recommended to install a database manageent tool like ``phppgadmin``.

Some additional information:

    * `This <https://help.ubuntu.com/community/PostgreSQL/>`_ is a good tutorial from the Ubuntu Community on how to set up PostgreSQL to use with the HRM.


Disable SElinux
===============

HRM needs access to several operations that are blocked by SElinux.

.. tabs::
    .. tab:: Debian

       By default SElinux **is disabled**. In case SElinux has been enabled
       edit file ``/etc/selinux/config`` and update the following variable.

       .. code-block:: sh

           SELINUX=permissive

    .. tab:: RHEL

       By default SElinux **is enabled**. Edit file ``/etc/selinux/config`` to
       update the following variable.

       .. code-block:: sh
           
            SELINUX=permissive


.. note::

    Restart the machine after changing the value of SElinux.


Sendmail (postfix)
==================

HRM uses the PHP ``mail()`` function to notify the users:

    "For the Mail functions to be available, PHP must have access to the sendmail binary on your system during compile time. If you use another mail program, such as qmail or postfix, be sure to use the appropriate sendmail wrappers that come with them." `More... <http://www.php.net/mail>`_

.. tabs::
    .. code-tab:: bash Debian

        sudo apt install postfix

    .. code-tab:: bash RHEL

        sudo dnf install postfix

.. note::

    If your mail server is set up correctly and still PHP cannot send e-mails, SELinux might be blocking it. Query the status of ``httpd_can_sendmail`` as follows:

    ``$ /usr/sbin/getsebool httpd_can_sendmail``

    If ``httpd_can_sendmail`` is ``off``, you can enable it with:

    ``$ /usr/sbin/setsebool -P httpd_can_sendmail on``


PHP `date()` and default timezone
---------------------------------

Please make sure to set the default timezone in `php.ini` as follows:

.. code-block:: sh

    [Date]
    ; Defines the default timezone used by the date functions
    ; http://php.net/date.timezone
    date.timezone = "Europe/Zurich"

Otherwise you will get the following warning every time the PHP function `date()` is called within the HRM:

::

    PHP Warning: date(): It is not safe to rely on the system's timezone settings. You are
    required to use the date.timezone setting or the date_default_timezone_set() function. (...)

Click here for the `full list of supported time zones <http://us2.php.net/manual/en/timezones.php>`_.


SSH
===

If the queue manager and the image processing server are not on the same machine (see installation instructions), HRM transfers files via ssh between the two using ``sudo``. To allow HRM to login and run commands as sudo via remote, it is necessary to comment out the line ``'Defaults requiretty'`` in the ``/etc/sudoers`` file.


Compressors
===========

The HRM compresses files to be downloaded (such as deconvolution results). Several options are possible (and more can be added in the configuration files), but by default the HRM uses ``zip``.

.. tabs::

    .. code-tab:: bash Debian

        .. code-block:: sh

            sudo apt install zip

    .. code-tab:: bash RHEL

            sudo dnf install zip


.. _prerequisites-omero:


(Optional) OMERO support
========================

For using the :ref:`omero_configuration`, you will need to install the corresponding
Python package. Please refer to the `HRM-OMERO Connector project
<https://pypi.org/project/hrm-omero/>`_ for installation details.
