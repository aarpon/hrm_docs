.. include:: global_directives.inc

.. _connector_omero:

***************
OMERO connector
***************

For setting up the `HRM-OMERO Connector <https://pypi.org/project/hrm-omero/>`_ please
first follow the installation instructions from the project's documentation.

Then enable the OMERO connector by setting the value of ``$omero_transfers`` to ``true``
in ``$HRM_CONFIG/hrm_config.inc``.

.. code-block:: php

    <?php
    ...
    //======================================================================
    // HRM + OMERO
    //======================================================================

    // Switch on/off (true/false) data transfers between HRM and OMERO.
    $omero_transfers = true;

    ?>

In addition, the following values need to be set accordingly in
``/etc/hrm.conf``. By default, those settings are commented out, so make sure
to remove the comment sign ``#`` in front of those lines!

Assuming your OMERO instance is running on host ``omero.mynetwork.xy`` and is using the
default port ``4064``, this should look as shown below.

.. code-block:: sh

    # Interaction with OMERO (if switched on in hrm/config).
    OMERO_HOSTNAME="omero.mynetwork.xy"
    OMERO_PORT="4064"
