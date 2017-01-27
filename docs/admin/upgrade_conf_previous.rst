.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. _upgrade_conf_previous:

**************************************************
Update the configuration files (previous versions)
**************************************************

.. warning:: These instructions refer to older versions of HRM!

3.2 to 3.3
----------

The ``$change_ownership`` option is not supported in version **3.3** any more.
If the variable is present in the configuration files ``hrm_{server|client}_config.inc`` 
it will be silently ignored. For consistency reasons it is therefore recommend to remove this
setting from the config file(s).

Group authentication
--------------------

As of HRM 3.3, external authentication via :ref:`Active Directory <activedir_auth>` or :ref:`generic LDAP <ldap_auth>` now supports **group authorization**. An additional array ``$AUTHORIZED_GROUPS`` can be set to define the set of :ref:`Active Directory <activedir_auth>` or :ref:`generic LDAP <ldap_auth>` groups that are granted access to HRM.

3.1 to 3.2
----------

As of version 3.2 of HRM, the system users running the Queue Manager and the web server are expected to have direct read-write access to the data folders. If this is not the case for your setup and you rely on adding the web server user to ``/etc/sudoers``, please notice that **this behavior is deprecated in 3.2 but can still be enabled** by adding:

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

