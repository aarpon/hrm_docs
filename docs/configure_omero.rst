.. include:: global_directives.inc

.. _connector_omero:

***************
OMERO connector
***************

Please make sure to have the :ref:`OMERO prerequisites <prerequisites-omero>`
set up correctly. To enable the OMERO connector, then set the
``$omero_transfers`` variable to ``true`` in ``$CONFIG/hrm_client_config.inc``
and in ``$CONFIG/hrm_server_config.inc``.

.. code-block:: php

    <?php
    ...
    //======================================================================
    // HRM + Omero 
    //======================================================================

    // Switch on/off (true/false) data transfers between HRM and Omero.
    $omero_transfers = true;

    ?>

In addition, the following values need to be set accordingly in
``/etc/hrm.conf``. Assuming your OMERO server is running on a host called
``omero.mynetwork.xy`` and using the versions shown in the example in the
:ref:`OMERO prerequisites <prerequisites-omero>`, this would look as below.
Please make sure to adjust ``OMERO_PKG`` and ``OMERO_HOSTNAME`` so it is
matching your current setup.

.. code-block:: sh
    
    # Interaction with OMERO (if switched on in hrm/config).
    OMERO_PKG="/opt/OMERO/OMERO.server-5.0.3-ice34-b41.linux"
    OMERO_HOSTNAME="omero.mynetwork.xy"
    OMERO_PORT="4064"
