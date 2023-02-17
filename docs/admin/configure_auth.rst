.. include:: global_directives.inc

.. _configure_auth:

************************
Configure authentication
************************

The HRM curently supports three user authentication mechanisms:

* Simple, internal user management module (default - no additional configuration needed)
* Generic `LDAP <http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol>`_ server
* Microsoft's Active Directory - (`AD <http://en.wikipedia.org/wiki/Active_Directory>`_) server

The HRM can be configured to use LDAP/AD to test user credentials and obtain limited user information (e-mail address angd group).

You can enable any combination of authentication mechanisms by editing ``$HRM_CONFIG/hrm_config.inc``.
The first one is the default for new users. Valid examples are:

.. code-block:: php

    <?php
    ...
    // Only integrated authentication (default)
    $authenticateAgainst = array("integrated");

    // Authenticate against Active Directory by default; 
    // some users may be checked against integrated authentication
    $authenticateAgainst = array("active_dir", "integrated");

    // Integrated authentication by default; 
    // some users may be authenticated against ldap
    $authenticateAgainst = array("integrated", "ldap");

    // This is also possible, however unlikely in reality:
    $authenticateAgainst = array("active_dir", "ldap", "integrated");
    ...

The following pages explain the required configuration steps for the support authentication mechanisms.

.. toctree::
   :maxdepth: 1

   configure_auth_activedir
   configure_auth_ldap
   