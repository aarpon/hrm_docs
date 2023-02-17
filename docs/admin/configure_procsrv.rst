.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

**************************************
Review processing server configuration 
**************************************

In the table ``server`` of the HRM database, two default values are set for the fields name (i.e. the name of the server running Huygens Core) and huscript_path (i.e. the path pointing to the hucore executable).

``name`` has default value ``localhost``, but can also be something like ``remote.server.com``.
``huscript_path`` has default value ``/usr/local/bin/hucore``.

If you need to change the default values, you can use your favorite SQL client and execute a query similar to this (for MySQL):

.. code-block:: sql

    UPDATE server SET name = 'remote.server.com', huscript_path = '/usr/bin/hucore';

.. note::

    The HRM requires the ``hucore`` binary to work, not ``huscript``. Before hucore was introduced HRM was indeed using ``huscript``; the ``huscript_path`` entry in the database was kept not to break existing HRM installations.

.. warning::

    The server table contains two other entries: ``status`` and ``job``. These are used by the interface at runtime, please do not set them manually!
