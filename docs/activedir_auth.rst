.. include:: global_directives.inc

.. _activedir_auth:

*******************************
Active Directory authentication
*******************************

To enable Active Directory authentication, please set the ``$authenticateAgainst`` variable to "ACTIVE_DIR" in ``$HRM_CONFIG/hrm_client_config.inc`` and in ``$HRM_CONFIG/hrm_server_config.inc``

.. code-block:: php

    <?php
    ...
    // Authentication type: MYSQL, ACTIVE_DIR or LDAP
    $authenticateAgainst = "ACTIVE_DIR";
    ...

Then, copy ``$HRM_SAMPLES/active_directory.config.inc.sample`` to ``$HRM_CONFIG/active_directory.config.inc`` and edit it.

.. code-block:: php

    <?php
    // This file is part of the Huygens Remote Manager
    // Copyright and license notice: see license.txt

    // See http://adldap.sourceforge.net/wiki/doku.php?id=api_configuration for
    // detailed help on configuring adLdap.

    // The account suffix for your domain
    $ACCOUNT_SUFFIX = "@mydomain.local";
    
    // The base dn for your domain
    $BASE_DN = "DC=mydomain,DC=local"; 
    
    // Array of domain controllers. Specifiy multiple controllers if you would
    // like the class to balance the LDAP queries amongst multiple servers
    $DOMAIN_CONTROLLERS = array ("dc01.mydomain.local");

    // Domain controller port
    $AD_PORT = 389;

    // User name suffix
    $AD_USERNAME_SUFFIX = "";

    // User name suffix matching string
    $AD_USERNAME_SUFFIX_REPLACE_MATCH = "";

    // User name suffix replacing string
    $AD_USERNAME_SUFFIX_REPLACE_STRING = "";

    // Optional account with higher privileges for searching (otherwise
    // leave it to NULL). This should be set to a domain admin account (only
    // read operations are performed!)
    $AD_USERNAME = NULL;
    $AD_PASSWORD = NULL;
    
    // Tweak to get the real primary group from Active Directory. It works if
    // the user's primary group is domain users.
    // http://support.microsoft.com/?kbid=321360
    $REAL_PRIMARY_GROUP = true;
    
    // Use SSL (LDAPS)
    $USE_SSL = false;
    
    // Use TLS: if you wish to use TLS you should ensure that $USE_SSL is 
    // set to false and vice-versa
    $USE_TLS = false;
    
    // When querying group memberships, do it recursively 
    $RECURSIVE_GROUPS = true;

    // Users usually belong to several groups. GROUP_INDEX defines
    // which level of the hierarchy to consider (starts by 0). This
    // obviously assumes that the sequence of groups memberships is
    // constant among users. Set $GROUP_INDEX to -1 to get an array
    // with all groups for the user. Please notice that this can also
    // be used in combination with the next parameter.
    $GROUP_INDEX = 0;

    // If there is no way to get the desired group by using $GROUP_INDEX,
    // this is an additional little trick. For this to work, $GROUP_INDEX
    // MUST be set to -1, and the following array must contain the list of
    // valid groups to be considered. This way, for each user the complete
    // list of groups will be returned from the Active Directory, and of
    // those, the one that is contained in the following array will be picked.
    // If more than one matching group is found, the first will be taken. If
    // no match is found, all groups will be returned.
    // Fill the array as follows: $VALID_GROUPS = array( "group1", "group2" )
    // with as many groups as you need.
    $VALID_GROUPS = array( );    

Special case: Active Directory forests
======================================

.. warning::

    For most installations, you can skip the entire rest of this section and
    proceed with the next one by simply leaving the variables
    ``$AD_USERNAME_SUFFIX``, ``$AD_USERNAME_SUFFIX_REPLACE_MATCH`` and
    ``$AD_USERNAME_SUFFIX_REPLACE_STRING`` with their default values (empty,
    i.e. ``""``).

This part of the config is meant for the special case of an Active Directory
with multiple domains (commonly referred to as `forest`) which usually consist
of a top-level domain (the `forest root` domain) and several sub-domains. If
the HRM users belong to domains in all levels of the forest it would be
required to enter the full domain name for logging in, which can become quite
tedious (and therefore error-prone).

Consider the following domain setup, a root domain called ``SATURN`` with two
sub-domains ``RHEA`` and ``TETHYS``. Those "plain" domain names are usually
referred to as `NetBIOS Domain Names`. A hierarchical representation could look
like this:

.. code-block:: sh

    SATURN
      |
      +-- RHEA
      |
      +-- TETHYS

Now, assuming a top-level suffix of ``.private``, in Microsoft's Active
Directory naming scheme this is translated into fully qualified domain names
(FQDN's) as follows. The `root` domain (SATURN) gets prefixed by ``ads.`` and
followed by the top-level ``.private`` suffix, whereas the two subdomains just
get postfixed by the FQDN of the root domain. The graphical representation from
above would therefore translate into this:

.. code-block:: sh

    ads.saturn.private
      |
      +-- rhea.ads.saturn.private
      |
      +-- tethys.ads.saturn.private


To make authentication work in such a scenario, it is required to authenticate
against the `GLOBAL CATALOG` of the Active Directory. This is an LDAP service
provided `only` on the domain controllers of the `root` domain on the special
port ``3268``. The usernames used to authenticate have to be of the form
``username@fully.qualified.domain.name`` to provide the global catalog with the
information to which sub-domain a certain account belongs as it is possible to
have the same username for different accounts in different domains of a single
domain forest.

Now given the HRM configuration option ``$ACCOUNT_SUFFIX`` would be set to
``.saturn.private``, a user ``foo`` from the domain ``SATURN`` could log in
using something like ``foo@ads`` whereas a user ``bar`` from ``RHEA`` would
have to type ``bar@rhea.ads``. This is obviously screaming for problems as
normal users don't understand where and why to put those weird suffixes,
especially as they've never heard of something like ``ads`` before.

Using the sample config from below, users can simply log on by using their
regular account name followed by an ``@`` sign and the (short) NetBIOS domain
name, e.g.

    `foo@saturn`

or

    `bar@rhea`

which is way easier to explain and remember for them, especially as the short
domain names are usually visible for them when logging into their workstation.

.. code-block:: php

    <?php
    ...
    $ACCOUNT_SUFFIX = "";
    $BASE_DN = "DC=ads, DC=saturn, DC=private";

    // set this to a domain controller of the *ROOT* domain:
    $DOMAIN_CONTROLLERS = array("dc01.ads.saturn.private");

    // the port is required to connect to the global catalog:
    $AD_PORT = 3268;

    // give the FQDN of the root domain with a leading dot here:
    $AD_USERNAME_SUFFIX = ".ads.saturn.private";

    // account names from the root domain will end up wrong, looking like this
    // (note the leading "@" and the double occurence of the root domain):
    $AD_USERNAME_SUFFIX_REPLACE_MATCH = "@saturn.ads.saturn.private";

    // they have to be rewritten using the correct suffix instead (removing the
    // first occurence of the root domain name):
    $AD_USERNAME_SUFFIX_REPLACE_STRING = "@ads.saturn.private";
    ?>

Please feel free to contact the HRM developers in case you need help setting up
authentication in a multi-domain forest scenario!
