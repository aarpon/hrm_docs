.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. _configure_permissions:

Set up HRM user and group and set permissions
=============================================

In the following instructions, ``HRM_DATA`` points to the data folder that contains all user subfolders (for example: ``/data/hrm_data``) and ``HRM_LOG`` is the log folder for the HRM (for example: ``/var/log/hrm``). Please see also the :ref:`conventions <conventions>`. It is important that those folder have the correct ownership and permissions set for HRM to work properly. Please follow these steps.

Create a Unix group ``hrm`` and user ``hrm`` on the web server machine.

.. code-block:: sh

    $ sudo groupadd --system hrm
    $ sudo useradd hrm --system --gid hrm --create-home

Make sure the log and data directories exist:

.. code-block:: sh

    sudo mkdir -pv ${HRM_DATA}
    sudo mkdir -pv ${HRM_LOG}

Make sure ``hrm`` owns (and has full read-write access) to HRM_DATA and HRM_LOG.
This is done by setting the group ownership of HRM_DATA and HRM_LOG to ``hrm``:

.. code-block:: sh

    sudo chown -R hrm:hrm ${HRM_DATA}
    sudo chmod -R u+s,g+ws ${HRM_DATA}
    sudo chown -R hrm:hrm ${HRM_LOG}
    sudo chmod -R u+s,g+ws ${HRM_LOG}

Add the Apache user to the ``hrm`` group:

.. tabs::
    .. tab:: Debian

        .. code-block:: sh

            sudo usermod www-data --append --groups hrm

    .. tab:: RHEL

        .. code-block:: sh

            sudo usermod apache --append --groups hrm

Finally restart your web server for the group changes to be activated.

.. tabs::
    .. tab:: Debian

        .. code-block:: sh

            sudo systemctl restart apache2.service

    .. tab:: RHEL

        .. code-block:: sh

            sudo systemctl restart httpd.service