.. include:: global_directives.inc

.. _configure_auth_ldap:

*******************
LDAP authentication
*******************

To enable LDAP authentication, please add "ldap" to the ``$authenticateAgainst`` array in ``$HRM_CONFIG/hrm_config.inc``

.. code-block:: php

    <?php
    ...
    $authenticateAgainst = array("ldap");
    ...

Then, copy ``$HRM_SAMPLES/ldap.config.inc.sample`` to ``$HRM_CONFIG/ldap.config.inc`` and edit it.

.. code-block:: php

    <?php
    // This file is part of the Huygens Remote Manager
    // Copyright and license notice: see license.txt

    // The machine on which the ldap server is running
    $ldap_host = "localhost";

    // The port for the ldap connection
    $ldap_port = "389";

    // Use SSL (LDAPS)
    $ldap_use_ssl = false;

    // Use TLS: if you wish to use TLS you should ensure that $ldap_use_ssl is
    // set to false and vice-versa
    $ldap_use_tls = false;

    // The ldap root
    $ldap_root = "dc=root,dc=country";

    // The base for the manager DN (either cn or uid)
    $ldap_manager_base_DN = "cn";

    // The ldap manager (username only!)
    $ldap_manager = "manager";

    // The ldap manager password
    $ldap_password = "secret";

    // The ldap manager OU: use this in case the ldap_manager is in some special OU
    // that distinguishes it from the other users. $ldap_manager_ou will be
    // prepended to $ldap_user_search_DN.
    // Set it to "" if $ldap_user_search_DN can be used for binding
    $ldap_manager_ou = "ou=special_user";

    // The user search DN (without ldap root)
    $ldap_user_search_DN = "cn=users";

    // Group filtering and authorization.
    //
    // Users in LDAP usually belong to several groups. Many of those groups
    // will not be relevant for the administrator of the HRM (groups like 'Domain Users',
    // 'Building 12', 'Staff') and the important ones, like the research group, are hidden
    // somewhere in this list.
    //
    // The $ldap_valid_groups array can be used to specify only those groups that are
    // interesting for the HRM and that will be used as the user group in the HRM and will
    // show up in the usage statistics. For example, only the research groups at the institution
    // might be included in this list.
    //
    // Additionally, not all research groups might be allowed to use the HRM. The 
    // $ldap_authorized_groups array can be used to specify those groups that are allowed
    // to use the HRM.
    //
    // Please notice that $ldap_authorized_groups must not strictly be a subset of 
    // $ldap_valid_groups.
    //
    // Example 1
    // =========
    //
    // $ldap_authorized_groups = array('group_einstein', 'group_bohr');
    // $ldap_valid_groups = array('group_einstein', 'group_bohr');
    //
    // User 'john' has groups {'Domain Users', 'Building 12', 'Staff', 'group_einstein'}
    //
    // 'john' is allowed to log in and the group used in HRM is 'group_einstein'.
    //
    // User 'stephanie' has groups {'Domain Users', 'Building 12', 'Staff', 'group_bohr'}
    //
    // 'stephanie' is allowed to log in and the group used in HRM is 'group_bohr'.
    //
    // User 'jeff' has groups {'Domain Users', 'Building 1', 'Admin Staff', 'group_admin'}
    //
    // 'jeff' is not allowed to log in ('group_admin' is not in $ldap_authorized_groups)'.
    //
    // Example 2
    // =========
    //
    // $ldap_authorized_groups = array('hrm');
    // $ldap_valid_groups = array('group_einstein', 'group_bohr');
    //
    // User 'john' has groups {'Domain Users', 'Building 12', 'Staff', 'group_einstein', 'hrm'}
    //
    // 'john' is allowed to log in and the group used in HRM is 'group_einstein'.
    //
    // User 'stephanie' has groups {'Domain Users', 'Building 12', 'Staff', 'group_bohr'}
    //
    // 'stephanie' is not allowed to log in (she does not belong to group 'hrm').
    //
    // User 'jeff' has groups {'Domain Users', 'Building 1', ''Admin Staff', 'group_admin'}
    //
    // 'jeff' is not allowed to log in (she does not belong to group 'hrm').
    //
    // Example 3
    // =========
    //
    // $ldap_authorized_groups = array();
    // $ldap_valid_groups = array('group_einstein', 'group_bohr');
    //
    // No restriction on which groups can log in to HRM. Group filtering works as in Examples 1
    // and 2.
    //
    // Example 4
    // =========
    //
    // $ldap_authorized_groups = array();
    // $ldap_valid_groups = array();
    //
    // If neither valid nor authorized groups are defined, all groups are allowed to log in and
    // the first returned group will be used in HRM.
    //
    // User 'john' has groups {'Domain Users', 'Building 12', 'Staff', 'group_einstein', 'hrm'}
    //
    // john's group in HRM will be 'Domain Users'.
    //
    // Example 5
    // =========
    //
    // $ldap_authorized_groups = array(... any number of entries ...);
    // $ldap_valid_groups = array();
    //
    // If $ldap_valid_groups is empty and $ldap_authorized_groups contains one or more entries,
    // $ldap_valid_groups will be reset to be the same as $ldap_authorized_groups (the end 
    // behavior will be as in Example 1).

    // Groups to use in HRM (filter)
    $ldap_valid_groups = array();

    // Groups authorized to log in to HRM.
    $ldap_authorized_groups = array();
