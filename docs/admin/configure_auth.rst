.. include:: global_directives.inc

************************
Configure authentication
************************

The HRM curently supports three user authentication mechanisms; if your institution relies on `Microsoft's Active Directory <http://en.wikipedia.org/wiki/Active_Directory>`_ or a generic `LDAP server <http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol>`_, the HRM can be configured to use them to test user credentials and obtain limited user information (e-mail address angd group). Otherwise, the HRM implements a simple, internal user management module.

You can enable any combination of authentication mechanisms. The first one is the default for new users. Valid examples are:

.. code-block:: php

    <?php
    ...
    // Only integrated authentication
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

   internal_auth
   activedir_auth
   ldap_auth
   