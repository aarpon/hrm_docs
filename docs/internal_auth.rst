.. include:: global_directives.inc

***********************
Internal authentication
***********************

To enable Active Directory authentication, please set the ``$authenticateAgainst`` variable to "MYSQL" in ``$CONFIG/hrm_client_config.inc`` and in ``$CONFIG/hrm_server_config.inc``

.. code-block:: php

    <?php
    ...
    // Authentication type: MYSQL, ACTIVE_DIR or LDAP
    $authenticateAgainst = "MYSQL";
    ...

This is the default value, so nothing needs to be changed in a fresh installation to use internal authentication.

.. note::

    Please notice that you should use ``"MYSQL"`` even if you are using PostgreSQL as your database backend!

