.. include:: global_directives.inc

***********************
Internal authentication
***********************

To enable internal authentication, please add "integrated" to the ``$authenticateAgainst`` array in ``$HRM_CONFIG/hrm_config.inc``

.. code-block:: php

    <?php
    ...
    $authenticateAgainst = array("integrated");
    ...

This is the default value, so nothing needs to be changed in a fresh installation to use internal authentication.
