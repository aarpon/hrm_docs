.. include:: global_directives.inc

.. _`configure-database`:

***********************
Set up the HRM database
***********************

Preparing the database for the HRM consists of two steps, first the
corresponding user needs to be created and configured and then the database
itself has to be created and prepared for the HRM.

Create the HRM database user
============================

Unless the database user for the HRM is already existing, you need to create it
and assign the corresponding permissions.

MySQL
-----

.. note::

    On Ubuntu 22.04 LTS and newer you might need to follow `these instructions to set
    the mysql root password <https://linuxhint.com/change-mysql-password-ubuntu-22-04/>`_.


The following command will create a new MySQL user ``hrm`` and grant the
permissions to a database ``hrm@localhost`` using the ``mysql`` command line
tool. Of course, you can also use a database management tool like
``phpmyadmin`` to perform this task if you prefer. Make sure to adjust the
password for the new database user so it matches the one from your
configuration files.

.. code-block:: sh

    # start the mysql command line client and connect as root:
    mysql -u root -p
    # Create the database if it does not exist yet:
    CREATE DATABASE hrm CHARACTER SET utf8;
    # now from within the client, create the database user:
    CREATE USER 'hrm'@'localhost' IDENTIFIED BY 'dbpasswd';
    # grant permissions to the user:
    GRANT ALL ON hrm.* to 'hrm'@'localhost';
    exit;

PostgreSQL
----------

.. code-block:: sh

    su postgres -c "createuser -e -P -d -A -S -R hrm"
    su postgres -c "createdb hrm"

RHEL

MD5 host authentication has to be enabled explicitly on RHEL systems.
This can be done using the following commands:

.. code-block:: sh

    sudo -s
    echo -e "host all hrm 127.0.0.1/32 md5\n" >> /var/lib/pgsql/data/pg_hba.conf
    echo -e "host all hrm ::1/127 md5\n" >> /var/lib/pgsql/data/pg_hba.conf
    service postgresql restart


.. _`create-database`:

On Ubuntu MD5 host authentication is enabled by default.

Create or update the database
=============================

Run the php script ``$HRM_SETUP/dbupdate.php`` from the shell to create and
populate the HRM database. The same command can be used to perform an upgrade
of the database when the HRM version is upgraded:

.. code-block:: sh

    cd $HRM_SETUP
    php dbupdate.php

If the database does not exist, it will be created using the information stored in the ``$HRM_CONFIG/hrm_config.inc`` and filled with content for the latest revision. If it exists, it will be updated from whichever revision it currently has.


.. note::

    MySQL 8+ might return the following error: 'The server requested
    authentication method unknown to the client'.
    Which can be fixed by

.. code-block:: sh

   # Start the mysql command line client and connect as root:
   mysql -u root -p
   # Notify MySQL that the HRM user logs in with a password.
   ALTER USER '$HRMUSER'@'localhost' IDENTIFIED WITH mysql_native_password BY
   '$HRMUSERPASSWORD';
   FLUSH PRIVILEGES;
   exit;
