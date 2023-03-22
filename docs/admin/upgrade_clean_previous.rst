.. include:: global_directives.inc

.. _upgrade_clean_previous:

***************************************************
Clean up previous installations (previous versions)
***************************************************

.. warning:: These instructions refer to older versions of HRM!

3.4 and newer
-------------

It is highly recommended **not to extract the new archive on top of the old one**. 

Please rename the old hrm folder, extract the code into a fresh ``${HRM_ROOT}`` and move the configuration files from the old ``config`` subfolder into the new ``${HRM_ROOT}/config``.   

You might also want to :ref:`reinstall <hrm_daemon>` the ``hrmd`` or ``hrmd.service`` scripts.

3.3 to 3.4
----------

In version 3.4, we started a major reorganization of the code structure of HRM and it is therefore highly recommended **not to extract the new archive on top of the old one**. 

Please rename the old hrm folder, extract the code into a fresh ``${HRM_ROOT}`` and move the configuration files from the old ``config`` subfolder into the new ``${HRM_ROOT}/config``.   

You might also want to :ref:`reinstall <hrm_daemon>` the ``hrmd`` or ``hrmd.service`` scripts.

3.2 to 3.3
----------

HRM 3.3 uses new init scripts. Please delete the old files
``$HRM_BIN/hrm_user_manager``, ``$HRM_BIN/hrm_user_manager_old``,
``$HRM_BIN/hrmd`` and ``$HRM_BIN/ome_hrm`` and then follow the instructions in
:ref:`Upgrade the init script <upgrade_the_init_script>`.

.. _upgrade_the_init_script:

Upgrade the init script
=======================

.. note:: If your Linux installation is using the ``systemd`` init system,
          please have a look at the :ref:`instructions about how to set up the
          HRM daemon with systemd <install_hrmd_systemd>`. Please make sure to
          remove the old init script at ``/etc/init.d/hrmd`` in this case!

          Otherwise, proceed as described here for the init script.

This step is basically identical to the initial installation of the init script
as described in :ref:`installing the daemon <hrm_daemon>`. You need to copy the
new script from ``$HRM_RESRC/sysv-init-lsb/hrmd`` to ``/etc/init.d/`` and make
sure it is executable. This can be done using the following commands:

.. code-block:: sh

    sudo cp -v $HRM_RESRC/sysv-init-lsb/hrmd /etc/init.d/hrmd
    sudo chmod +x /etc/init.d/hrmd

.. _update_hrm_data_permissions_previous:

Update the data folder permissions
==================================

As of HRM 3.2.0, the system users running the Queue Manager and the web server
are expected to have full read-write access to ``$HRM_DATA``. The supported way
of doing this is explained in :ref:`setting up the HRM user and group
<configure_permissions>`. Briefly:

  * a user ``hrm`` and its corresponding group ``hrm`` are created
  * the web server user (|ubuntu| ``www-data``, RHEL ``apache``) is added
    to the ``hrm`` group
  * the variable ``SUSER`` is set to ``hrm`` in /etc/hrm.conf
  * the ``$HRM_DATA`` and ``$HRM_LOG`` group ownership is set to ``hrm`` with
    the ``setgid`` bit set

For detailed instructions, please see :ref:`setting up the HRM user and group
<configure_permissions>`.

.. warning:: With **HRM 3.2** it was possible to preserve the old behavior by
             setting a configuration variable ``$change_ownership``. This is
             not supported with **HRM 3.3** any more!

3.1 to 3.2
----------

.. code-block:: sh

    rm -v inc/ActiveDirectory.inc.php inc/Ldap.inc.php

