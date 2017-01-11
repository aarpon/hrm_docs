.. include:: global_directives.inc

.. warning:: As of version 3.2.0, the HRM expects specific file permissions on the file area! Please see :ref:`update_hrm_data_permissions` below. The deprecated fall-back mechanism of version 3.2 **no longer works in 3.3 and 3.4**!

***************
Version upgrade
***************

If you have upgraded the HRM in the past, you will know that some steps must be performed in addition to replacing the old HRM code with the new one: some entries might have been added or changed in the configuration files (``hrm_{server|client}_config.inc``), and the database structure might have been changed.

Stop the Queue Manager
======================

Significant parts of the configuration as well as the database are usually changed during an upgrade, so the Queue Manager needs to be stopped first.

Shut down the Queue Manager with:

.. code-block:: sh

    sudo /etc/init.d/hrmd stop

if you are using :ref:`System-V or upstart <install_hrmd_sysv>`, or with:

.. code-block:: sh

  sudo systemctl stop hrmd.service

if you are using :ref:`systemd <install_hrmd_systemd>`.

In some rare situations, the Queue Manager might get stuck. To ensure the *stop* command did work properly, run the following check.

On System-V or upstart:

.. code-block:: sh

    sudo /etc/init.d/hrmd status

On systemd:

.. code-block:: sh

    sudo systemctl status hrmd.service

Alternatively, you can use:

.. code-block:: sh

  ps aux | grep -i [r]unHuygens

that should return empty (nothing).

Download and extract the new HRM release
========================================

To install the new HRM version you need to download the ``.zip`` file from
the website or github as explained in :ref:`downloading the standard archive
<download-hrm-standard>`.

.. warning::

  Please do not extract the new archive on top of the previous HRM installation! See details below.

Clean up previous installations
===============================

In version 3.4, we started a major reorganization of the code structure of HRM and it is therefore higly recommended **not to extract the new archive on top of the old one**. 

Please rename the old hrm folder, extract the code into a fresh ``${HRM_ROOT}`` and move the configuration files from the old ``config`` subfolder into the new ``${HRM_ROOT}/config``.   

You might also want to :ref:`reinstall <hrm_daemon>` the ``hrmd`` or ``hrmd.service`` scripts.

.. note:: Please follow :ref:`these instructions <upgrade_clean_previous>` **first** if you are upgrading from older versions.

Update the configuration files
==============================

$authenticateAgainst
--------------------

The support for various :ref:`authentication mechanisms <configure_auth>` was extended in HRM 3.4. This comes with a change 
in configuration: the  ``$authenticateAgainst`` variable is **now an array** and its values have also changed (although, temporarily, 
the old ones are still supported). Example:

.. code-block:: php

  <?php
  ...
  $authenticateAgainst = array("active_dir", "integrated");
  ...

$useDESEncryption
-----------------

The configuration variable ``$useDESEncryption`` (that was not used) must be removed from the configuration files!

.. note:: Please follow :ref:`these instructions <upgrade_conf_previous>` **first** if you are upgrading from older versions.

Check the configuration files
=============================

An easy way to check for modifications is by running the ``$HRM_HOME/resources/checkConfig.php`` script. From the shell, run:

.. code-block:: sh

    cd $HRM_HOME
    php resources/checkConfig.php config/hrm_server_config.inc
    php resources/checkConfig.php config/hrm_client_config.inc

Checking the 3.3 files with the 3.4.x ``checkConfig.php`` script will result in the following output:

.. code-block:: sh

  Check against HRM v3.4.x.
  * * * Error: variable useDESEncryption must be removed from the configuration files!
  * * * Error: variable 'authenticateAgainst' must be an array!
  * * * Moreover, please change 'MYSQL' into 'integrated'.
  Check completed with errors! Please fix your configuration!

Please make sure to fix all problems. The sample files and the :ref:`manual_install` instructions will help you set the correct parameters.

.. note:: Please follow :ref:`these instructions <upgrade_check_previous>` **first** if you are upgrading from older versions.

Update the database
===================

Newer versions of the HRM might use slightly different/updated versions of the database back-end than previous ones.

+-------------+------------------+
| HRM version | Database version |
+=============+==================+
| 3.4         | 15               |
+-------------+------------------+
| 3.3         | 14               |
+-------------+------------------+
| 3.2         | 13               |
+-------------+------------------+
| 3.1         | 12               |
+-------------+------------------+
| 3.0.3       | 11               |
+-------------+------------------+
| 3.0         | 10               |
+-------------+------------------+
| 2.1         | 9                |
+-------------+------------------+
| 2.0         | 8                |
+-------------+------------------+
| 1.2.3       | 7                |
+-------------+------------------+

For this reason, the first time you run the HRM after an update you will be told that the database must be updated and that you are not allowed to continue until this has been done!

.. note:: Database updates are supported across HRM versions, i.e. it is possible to upgrade the database from revision 7 to 15 in one step.

The following describes two possible ways to update the database.

.. note:: Although we test this procedure quite carefully, it is **highly recommended to backup the database before updating!**

Updating from the web interface
-------------------------------

Login to the HRM as the admin user: you will be brought directly to the Database update page. Click on the update button. If everything works properly (as it should...), the following message should be displayed.

.. code-block:: sh

    Needed database revision for HRM v3.4 is number 15.
    Current database revision is number 14.
    Updating...

    Database successfully updated to revision 15.

The database is now at the latest revision.

Updating from the console
-------------------------

Alternatively, the database can be updated from the console (see :ref:`create or update database <create-database>`). Please pay attention to what the update process will report! The output should be the same as the one listed in the previous section, but if the update fails, you might want to `report it <http://hrm.svi.nl:8080/redmine/projects/hrmdev/issues/new>`_.

Re-start the Queue Manager
==========================

After processing the described upgrade steps, the Queue Manager needs to be started again.

.. code-block:: sh

    sudo /etc/init.d/hrmd start

Upgrade from previous releases
==============================

The following pages are linked to from the relevant sections above, but are listed here again for convenience.

.. toctree::
    :maxdepth: 1

    upgrade_clean_previous
    upgrade_conf_previous
    upgrade_check_previous
