.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

.. _`hrm_conf`:

*************
Edit hrm.conf
*************

The ``hrm.conf`` file is used by both the Web server and the Queue Manager.

Copy the sample file
====================

The sample configuration file ``$SAMPLES/hrm.conf.sample`` must be copied to ``/etc/hrm.conf`` and then edited as explained in the following. 

Edit the configuration file
===========================

This is the content of the sample configuration file:

.. code-block:: sh

    #!/bin/bash
    #
    # HRM configuration file
    #
    # This file is part of the Huygens Remote Manager
    # Copyright and license notice: see license.txt

    # HRM install directory
    HRM_HOME="/path/to/hrm/home"

    # HRM image share
    HRM_DATA="/path/to/hrm/data"

    # Source and destination folder names
    HRM_SOURCE="huygens_src"
    HRM_DEST="huygens_dst"

    # User to run the HRM daemon with rights to
    # execute /bin/mkdir, /bin/chown, /bin/chmod and
    # /bin/rm on HRM_DATA (see above) for user management.
    SUSER="hrm"

    # HRM log directory
    HRM_LOG="/var/log/hrm"

    # Interaction with OMERO (if switched on in hrm/config).
    OMERO_SERVER_USER="omero"
    OMERO_HOME="/path/to/OMERO.server"

    # Set a custom PHP CLI binary if necessary:
    # PHP_CLI="/usr/local/php/bin/php"

Explanation
===========

- ``HRM_HOME`` points to ``$ROOT/hrm`` (for example: ``/var/www/html/hrm``).
- ``HRM_DATA`` points to the data folder that contains all user subfolders (for example: ``/data/hrm_data``).
- ``HRM_SOURCE`` and ``HRM_DEST`` are the source and destination subfolders inside the user directory (for example: ``src`` and ``dst``). The source folder for an hypothetical user 'john' would then be ``/data/hrm_data/john/src``.
- ``SUSER`` is the Unix user that runs the Queue Manager (for example: ``hrm``).
- ``HRM_LOG`` is the log folder for the HRM (for example: ``/var/log/hrm``)
- (optional) ``OMERO_SERVER_USER`` is the user running the OMERO server to interface with (for example: ``omero``)
- (optional) ``OMERO_HOME`` is the path to the OMERO.server executable (for example: ``/home/omero/omero/omero.server``)
- (optional) ``PHP_CLI`` is the path tho the php CLI executable if it is not in the path or another one should be used (for example: ``/usr/local/php/bin/php``).


