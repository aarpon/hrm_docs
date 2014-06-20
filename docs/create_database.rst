.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

.. _`create-database`:

*****************************
Create or update the database 
*****************************

Run the php script ``$SETUP/dbupdate.php`` from bash for the creation (or the update) of the HRM database:

.. code-block:: sh

    $ cd $SETUP
    $ php dbupdate.php

If the database does not exist, it will be created using the information stored in the ``$CONFIG/hrm_client_config.inc`` and filled with content for the latest revision. If it exists, it will be updated from whichever revision it currently has.
