.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. _hrm_user_group_perm:

Set up HRM user and group and set permissions
=============================================

In the following instructions, ``HRM_DATA`` points to the data folder that contains all user subfolders (for example: ``/data/hrm_data``) and ``HRM_LOG`` is the log folder for the HRM (for example: ``/var/log/hrm``). Please see also the :ref:`conventions <conventions>`. It is important that those folder have the correct ownership and permissions set for HRM to work properly. Please follow these steps.

Create a Unix group ``hrm`` and user ``hrm`` on the web server machine.

.. code-block:: sh

    $ sudo groupadd --system hrm
    $ sudo useradd hrm --system --gid hrm

Create the log directory:

.. code-block:: sh

    sudo mkdir ${HRM_LOG}

Make sure ``hrm`` owns (and has full read-write access) to HRM_DATA and HRM_LOG.
This is done by setting the group ownership of HRM_DATA and HRM_LOG to ``hrm``:

.. code-block:: sh

    sudo chown -R hrm:hrm ${HRM_DATA}
    sudo chmod -R u+s,g+ws ${HRM_DATA}
    sudo chown -R hrm:hrm ${HRM_LOG}
    sudo chmod -R u+s,g+ws ${HRM_LOG}

Add the Apache user (|ubuntu| www-data, |fedora| apache) to the ``hrm`` group:

.. code-block:: sh

    # www-data in Ubuntu, apache in Fedora
    sudo usermod www-data --append --groups hrm

.. note:: You might have to restart your server for the group changes to be activated.
