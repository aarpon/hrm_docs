.. include:: global_directives.inc

.. toctree::
   :maxdepth: 2


***************
Version upgrade
***************

If you have upgraded the HRM in the past, you will know that some steps must be performed in addition to replacing the old HRM code with the new one: some entries might have been added or changed in the configuration files, and the database structure might have been changed.

Upgrading the configuration files
=================================

2.1.x to 3.0
------------

From HRM 2.1.x to HRM 3.0, one variable was added in the configuration files.

::

  $omero_transfers={true|false}

1.2.x to 2.0
------------

From HRM 1.2.x to HRM 2.0, three variables were added in the configuration files:

::

  max_upload_limit
  max_post_limit
  email_list_separator

Moreover, three variables were removed:

::

    resultImagesOwnedByUser
    resultImagesRenamed
    enable_code_for_huygens


|note| If you are upgrading straight from HRM 1.2.x, please notice that as of HRM 2.0 configuration and sample files were moved as per following table.

======================  =======================  ======================  ======================
**Config files (new)**  **Sample files (new)**   **Config files (1.x)**  **Sample files (1.x)**
----------------------  -----------------------  ----------------------  ----------------------
HRM_ROOT/config         HRM_ROOT/config/samples  HRM_ROOT/inc            HRM_ROOT/resources
======================  =======================  ======================  ======================


Checking the configuration files
================================

An easy way to check for modifications is by running the `{HRM_ROOT}/resources/checkConfig.php` script. From the shell, run:

.. code-block:: sh

    $ cd $HRM_ROOT
    $ php resources/checkConfig.php config/hrm_server_config.inc

Replace `$HRM_ROOT` with the hrm root (e.g `/var/www/hrm`).

Checking the 2.1.x files with the 3.0 `checkConfig.php` script will result in the following output:

.. code-block:: sh

    Check against HRM v3.0.x.
    * * * Error: variable omero_transfers not set or empty.
    Check completed with errors! Please fix your configuration!

Checking the 1.2.x files with the 2.1.x `checkConfig.php` script will result in the following output:

.. code-block:: sh

    Check against HRM v2.1.x.
    * * * Error: variable max_upload_limit not set or empty.
    * * * Error: variable max_post_limit not set or empty.
    * * * Error: variable email_list_separator not set or empty. 
    * * * Error: variable resultImagesOwnedByUser must be removed from the configuration files!
    * * * Error: variable resultImagesRenamed must be removed from the configuration files! 
    * * * Error: variable enable_code_for_huygens must be removed from the configuration files! 
    Check completed with errors! Please fix your configuration!

Please make sure to fix all problems. The sample files and the :ref:`manual installation instructions <manual-install>` will help you set the correct parameters.

Updating the database
=====================

Newer versions of the HRM might use slightly different/updated versions of the database back-end than previous ones.

===========  ================
HRM version  Database version
-----------  ----------------
1.2.3        7
2.0          8
2.1          9
3.0          10
===========  ================

For this reason, the first time you run the HRM after an update you will be told that the database must be updated and that you are not allowed to continue until this has been done!

|note| Database updates are supported across HRM versions, i.e. it is possible to upgrade the database from revision 7 to 10 in one step.

The following describes two possible ways to update the database.

|note| Although we test this procedure quite carefully, it is **highly recommended to backup the database before updating!**

Updating from the web interface
-------------------------------

Login to the HRM as the admin user: you will be brought directly to the Database update page. Click on the update button. If everything works properly (as it should...), the following message should be displayed.

.. code-block:: sh

    Needed database revision for HRM v3.0 is number 10.
    Current database revision is number 9.
    Updating...

    Database successfully updated to revision 10.

The database is now at the latest revision.

Updating from the console
-------------------------

Alternatively, the database can be updated from the console (see here). Please pay attention to what the update process will report! The output should be the same as the one listed in the previous section, but if the update fails, you might want to `report it <http://hrm.svi.nl:8080/redmine/projects/hrmdev/issues/new>`_.

