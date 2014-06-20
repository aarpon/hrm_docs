.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

*************************
Install the prerequisites
*************************

The HRM requires a few prerequisites for its functions.

Operating system
================

The HRM should work on any recent Linux distribution, but in the bulk of this documentation we will explicitly address |ubuntu| **Ubuntu**. However, since we are planning to extend support to other distributions, additional information will incrementally appear over time. In the following you will already find some sections specific to |fedora| **Fedora** (that will apply to **RHEL** and **CentOS**).

|note| Please notice that with release 3.1, we drop support for |macosx| **Mac OS X**. HRM 3.0 is still known to work on Mac OS X from 10.5 (Leopard) onward, but no effort will be made to make future versions of the HRM compatible with Mac OS X. Also notice that the HRM was never tested on Mavericks.

Huygens Core
============

The HRM is an interface to Scientific Volume Imaging's `Huygens Core <http://www.svi.nl/HuygensCore>`_. **Huygens Core** is is a full compute engine intended to run image processing and deconvolution jobs on large 64 bit multiprocessor servers without a specific graphical interface (which is provided, in our case, by the HRM).

|note| If the web and the processing server are not on the same machine, you will need an additional Huygens Core for the web server with a **reader license** (free of charge).

Apache2 web server
==================

|ubuntu| Install **Apache2**

|macosx| The Apache2 web server is installed by default in Mac OS X. Please enable *Web sharing* in the System Preferences.

Web pages can be installed globally or per-user.

|ubuntu| The Apache2 global document root is ``/var/www``, or ``/var/www/html`` in more rectent versions. Users can put their pages in ``~/public_html``.

|macosx| The Apache2 global document root is ``/Library/WebServer/Documents`` (although it may vary). Users can put their pages in ``~/Sites``.

Apache2 access handling
-----------------------

HRM uses ``.htaccess`` files to prevent access to configuration files. Make sure to set the ``AllowOverride`` directive in ``/etc/apache2/sites-available/default`` to enable ``.htaccess`` files in the HRM on the web server (``AllowOverride All``), or at least make sure to prevent access to the subdirectories ``inc``, ``config``, ``run``, ``resources`` and ``setup``.

If you are installing the HRM in your user dir, make sure to change ``AllowOverride`` to ``All`` in ``/etc/apache2/mods-available/userdir.conf`` (make sure to enable the userdir mod first by running ``sudo a2enmod userdir`` in the shell).

|ubuntu| See also `Enabling use of Apache htaccess files <https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles>`_.

PHP |ge| 5.2
============

The HRM is made of two parts, a web interface and a queue manager, both written in PHP but with different requirements. The web interface requires the PHP 5 module for Apache2, the queue manager requires the PHP 5 command line interpreter.

|note| Minimum required PHP version is **5.2**.

|ubuntu| Install **libapache2-mod-php5**; **php5**; **php5-cli**; **php5-common**; **php5-mysql** (if you plan to use MySQL) or **php5-pgsql** (if you plan to use PostgreSQL; see also below); **php5-ldap** (optional, if you plan to use user authentication against LDAP or Microsoft's Active Directory).

Example (with MySQL): 

.. code-block:: sh

    $ sudo apt-get install libapache2-mod-php5, php5, php5-cli, php5-common, php5-mysql, php5-ldap

|fedora| Install **php**; **php-cli**; **php-common**; **php-mysql** (if you plan to use MySQL) or **php-pgsql** (if you plan to use PostgreSQL; see also below); **php-process**; **php-pdo**; **php-ldap** (optional, if you plan to use user authentication against LDAP or Microsoft's Active Directory).

Example (with MySQL):

.. code-block:: sh

    $ sudo yum install php, php-cli, php-common, php-mysql, php-process, php-pdo, php-ldap 

|macosx| The PHP 5 module for Apache2 and the PHP 5 command line interpreter are installed by default in Mac OS X. The PHP 5 module must be activated, though; uncomment the line:

.. code-block:: sh

    LoadModule php5_module libexec/apache2/libphp5.so

in the Apache2 configuration. Use ``vi``:

.. code-block:: sh

    $ sudo vi /private/etc/apache2/httpd.conf

Please also enable *Web sharing* in the System Preferences.

PHP `date()` and default timezone
---------------------------------

Please make sure to set the default timezone in `php.ini` as follows:

.. code-block:: sh

    [Date]
    ; Defines the default timezone used by the date functions
    ; http://php.net/date.timezone
    date.timezone = "Europe/Zurich"

otherwise you will get following warning every time the PHP function `date()` is called within the HRM:

::

    PHP Warning: date(): It is not safe to rely on the system's timezone settings. You are
    required to use the date.timezone setting or the date_default_timezone_set() function. (...)

Click here for the `full list of supported time zones <http://us2.php.net/manual/en/timezones.php>`_.

A relational database
=====================

The HRM officially supports two relational databases: **MySQL** and **PostgreSQL**.

MySQL
-----

|ubuntu| Install **php5-mysql**; install and configure **mysql-server**. Recommended: install **phpmyadmin**.

.. code-block:: sh

    $ sudo apt-get install php5-mysql, mysql-server

|fedora| TODO!

|macosx|  Download and install the `MySQL <http://dev.mysql.com/downloads/mysql/#downloads>`_ server.

To grant local access see `this page <http://www.svi.nl/PostgreSQLlocalAccess>`_.

PostgreSQL
----------

|ubuntu| Install **php5-pgsql**; install and configure **postgresql**. Recommended: install **phppgadmin**.

.. code-block:: sh

    sudo apt-get install php5-pgsql, postgresql, phppgadmin

|fedora| TODO!

|macosx| Download `PostgreSQL <http://www.enterprisedb.com/products-services-training/pgdownload#osx>`_ for MacOSX. Installation instructions can be found `on this page <http://www.enterprisedb.com/resources-community/pginst-guide>`_.

`This <http://www.cyberciti.biz/faq/howto-add-postgresql-user-account/>`_ is a good tutorial on how to create a user for the PostgreSQL database to use with the HRM.

To grant local access for users see `this page <http://www.svi.nl/PostgreSQLlocalAccess>`_.

Sendmail
========

HRM uses the PHP ``mail()`` function to notify the users: 

    "For the Mail functions to be available, PHP must have access to the sendmail binary on your system during compile time. If you use another mail program, such as qmail or postfix, be sure to use the appropriate sendmail wrappers that come with them. `Read more <http://www.php.net/mail>`_."

|ubuntu| Install and configure postfix.

.. code-block:: sh

    $ sudo apt-get install postfix

|fedora| TODO!

|macosx| mail works out of the box in Mac OS X.

SSH
===

If the queue manager and the image processing server are not on the same machine (see installation instructions), HRM transfers files via ssh between the two using ``sudo``. To allow HRM to login and run commands as sudo via remote, it is necessary to comment out the line ``'Defaults requiretty'`` in the ``/etc/sudoers`` file.

Compressors
===========

The HRM compresses files to be downloaded (such as deconvolution results). Several options are possible (and more can be added in the configuration files), but by default the HRM uses ``zip``.

|ubuntu| Install zip.

|fedora| TODO!

|macosX| zip is preinstalled.
