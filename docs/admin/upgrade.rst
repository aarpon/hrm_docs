.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. warning:: As of version 3.2.0, the HRM expects specific file permissions on the file area! Please see :ref:`update_hrm_data_permissions` below.

***************
Version upgrade
***************

If you have upgraded the HRM in the past, you will know that some steps must be performed in addition to replacing the old HRM code with the new one: some entries might have been added or changed in the configuration files (``hrm_{server|client}_config.inc``), and the database structure might have been changed.

Stop the Queue Manager
======================

Significant parts of the configuration as well as the database are usually changed during an upgrade, so the Queue Manager needs to be stopped first.

.. code-block:: sh

    sudo /etc/init.d/hrmd stop

In some rare situations, the Queue Manager might get stuck. To ensure the *stop* command did work properly, run the following check which should return empty:

.. code-block:: sh

    ps aux | grep -i [r]unHuygens

Download and extract the new HRM release
========================================

To install the new HRM version you need to download the ``.tar.gz`` file from
the website or github as explained in :ref:`downloading the standard archive
<download-hrm-standard>`.

The downloaded package then needs to be extracted inside the HRM's installation
directory, overwriting updated files but not touching your configuration files
etc. Assuming your downloaded version is ``3.2.0`` and you were placing the
package in your home directory, this can be done like this:

.. code-block:: sh

    cd $HRM_HOME
    tar xzf $HOME/hrm-3.2.0.tar.gz --strip=1

Cleaning up leftover files from previous installations
======================================================

Sometimes files were part of a previous release of the HRM but they are not
contained in the current one any more. With the above described method those
files don't get removed as only new files are extracted from the tar package.
To avoid cluttering up the installation they should be removed according to the
versions involved.

3.1 to 3.2
----------

.. code-block:: sh

    rm -v inc/ActiveDirectory.inc.php inc/Ldap.inc.php


Upgrade the init script
=======================

This step is basically identical to the initial installation of the init script
as described in :ref:`installing the daemon <hrm_daemon>`. You need to copy the
new script from ``$HRM_RESRC/hrmd_lsb-init`` to ``/etc/init.d/`` and make sure
it is executable. This can be done using the following commands:

.. code-block:: sh

    sudo cp -v $HRM_RESRC/hrmd_lsb-init /etc/init.d/hrmd
    sudo chmod +x /etc/init.d/hrmd

.. note:: There should be *NO* need to run ``update-rc.d`` to update the run-level links.

.. _update_hrm_data_permissions:

Update the data folder permissions
==================================

As of HRM 3.2.0, the system users running the Queue Manager and the web server
are expected to have full read-write access to ``$HRM_DATA``. The supported way
of doing this is explained in :ref:`setting up the HRM user and group
<setup_hrm_user_and_group>`. Briefly:

  * a user ``hrm`` and its corresponding group ``hrm`` are created
  * the web server user (|ubuntu| ``www-data``, |fedora| ``apache``) is added
    to the ``hrm`` group
  * the variable ``SUSER`` is set to ``hrm`` in /etc/hrm.conf
  * the ``$HRM_DATA`` and ``$HRM_LOG`` group ownership is set to ``hrm`` with
    the ``setgid`` bit set

For detailed instructions, please see :ref:`setting up the HRM user and group
<setup_hrm_user_and_group>`.

.. warning:: With **HRM 3.2** it was possible to preserve the old behavior by
             setting a configuration variable ``$change_ownership``. This is
             not supported with **HRM 3.3** any more!

Update the configuration files
==============================

3.2 to 3.3
----------

As stated in the previous section, the ``$change_ownership`` option is not
supported in version **3.3** any more. If the variable is present in the
configuration files ``hrm_{server|client}_config.inc`` it will be silently
ignored. For consistency reasons it is therefore recommend to remove this
setting from the config file(s).

3.1 to 3.2
----------

In version 3.2 of the HRM, the system users running the Queue Manager and the web server are expected to have direct read-write access to the data folders. If this is not the case for your setup and you rely on adding the web server user to ``/etc/sudoers``, please notice that **this behavior is obsolete in 3.2 but can still be enabled** by adding:

.. code-block:: php

    $change_ownership=true;

in ``hrm_{server|client}_config.inc``. The variable ``$change_ownership`` defaults to ``false`` if not explicitly set to true in the configuration, in compliance to the new behavior.

.. note:: As of **HRM 3.3**, this variable will be ignored and the new behavior will be **enforced**!
 
3.0.x to 3.1
------------

No changes in the configuration files.

2.1.x to 3.0
------------

From HRM 2.1.x to HRM 3.0, one variable was added in the configuration files.

.. code-block:: php

    $omero_transfers={true|false}

1.2.x to 2.0
------------

From HRM 1.2.x to HRM 2.0, three variables were added in the configuration files:

::

    [+] max_upload_limit
    [+] max_post_limit
    [+] email_list_separator

Moreover, three variables were removed:

::

    [-] resultImagesOwnedByUser
    [-] resultImagesRenamed
    [-] enable_code_for_huygens


.. note:: If you are upgrading straight from HRM 1.2.x, please notice that as of HRM 2.0 configuration and sample files were moved as per following table.

+----------------------+--------------------------+----------------------+----------------------+
| Config files (new)   | Sample files (new)       | Config files (1.x)   | Sample files (1.x)   |
+======================+==========================+======================+======================+
| $HRM_HOME/config     | $HRM_HOME/config/samples | $HRM_HOME/inc        | $HRM_HOME/resources  |
+----------------------+--------------------------+----------------------+----------------------+

Check the configuration files
=============================

An easy way to check for modifications is by running the ``$HRM_HOME/resources/checkConfig.php`` script. From the shell, run:

.. code-block:: sh

    cd $HRM_HOME
    php resources/checkConfig.php config/hrm_server_config.inc

Replace ``$HRM_HOME`` with the hrm root (e.g ``/var/www/hrm``).

Checking the 3.0.x files with the 3.1 ``checkConfig.php`` script will result in the following output:

.. code-block:: sh

    Check against HRM v3.1.x.
    Check completed successfully! Your configuration file is valid!

Checking the 2.1.x files with the 3.0 ``checkConfig.php`` script will result in the following output:

.. code-block:: sh

    Check against HRM v3.0.x.
    * * * Error: variable omero_transfers not set or empty.
    Check completed with errors! Please fix your configuration!

Checking the 1.2.x files with the 2.1.x ``checkConfig.php`` script will result in the following output:

.. code-block:: sh

    Check against HRM v2.1.x.
    * * * Error: variable max_upload_limit not set or empty.
    * * * Error: variable max_post_limit not set or empty.
    * * * Error: variable email_list_separator not set or empty. 
    * * * Error: variable resultImagesOwnedByUser must be removed from the configuration files!
    * * * Error: variable resultImagesRenamed must be removed from the configuration files! 
    * * * Error: variable enable_code_for_huygens must be removed from the configuration files! 
    Check completed with errors! Please fix your configuration!

Please make sure to fix all problems. The sample files and the :ref:`manual_install` instructions will help you set the correct parameters.

Update the database
===================

Newer versions of the HRM might use slightly different/updated versions of the database back-end than previous ones.

+-------------+------------------+
| HRM version | Database version |
+=============+==================+
| 1.2.3       | 7                |
+-------------+------------------+
| 2.0         | 8                |
+-------------+------------------+
| 2.1         | 9                |
+-------------+------------------+
| 3.0         | 10               |
+-------------+------------------+
| 3.0.3       | 11               |
+-------------+------------------+
| 3.1         | 12               |
+-------------+------------------+
| 3.2         | 13               |
+-------------+------------------+

For this reason, the first time you run the HRM after an update you will be told that the database must be updated and that you are not allowed to continue until this has been done!

.. note:: Database updates are supported across HRM versions, i.e. it is possible to upgrade the database from revision 7 to 13 in one step.

The following describes two possible ways to update the database.

.. note:: Although we test this procedure quite carefully, it is **highly recommended to backup the database before updating!**

Updating from the web interface
-------------------------------

Login to the HRM as the admin user: you will be brought directly to the Database update page. Click on the update button. If everything works properly (as it should...), the following message should be displayed.

.. code-block:: sh

    Needed database revision for HRM v3.2 is number 13.
    Current database revision is number 12.
    Updating...

    Database successfully updated to revision 13.

The database is now at the latest revision.

Updating from the console
-------------------------

Alternatively, the database can be updated from the console (see :ref:`create or update database <create-database>`). Please pay attention to what the update process will report! The output should be the same as the one listed in the previous section, but if the update fails, you might want to `report it <http://hrm.svi.nl:8080/redmine/projects/hrmdev/issues/new>`_.

Re-start the Queue Manager
==========================

After processing the described upgrade steps, the Queue Manager needs to be started again.

.. code-block:: sh

    sudo /etc/init.d/hrmd start
