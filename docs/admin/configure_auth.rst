.. include:: global_directives.inc

************************
Configure authentication
************************

The HRM curently supports three user authentication mechanisms; if your institution relies on `Microsoft's Active Directory <http://en.wikipedia.org/wiki/Active_Directory>`_ or a generic `LDAP server <http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol>`_, the HRM can be configured to use them to test user credentials and obtain limited user information (e-mail address angd group). Otherwise, the HRM implements a simple, internal user management module.

The following pages explain the required configuration steps for the support authntication mechanisms.

.. toctree::
   :maxdepth: 1

   internal_auth
   activedir_auth
   ldap_auth
   