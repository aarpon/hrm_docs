.. include:: global_directives.inc

.. _hrm_daemon:

************
Daemon setup
************

The HRM daemon consists of two parts, the actual queue manager (a PHP process)
and a shell-based wrapper in ``$HRM_BIN/hrm_queuemanager`` that prepares the
environment, checks the config, launches the queue manager and cleans up after
the process has terminated.

The configuration file for the HRM daemon is ``/etc/hrm.conf`` (see
:ref:`configure_hrm`)

.. warning::

    You should never start the PHP process directly as unpredicted effects will
    happen, in worst case including damage to the HRM database.

Depending on whether your Linux installation is using a "classical" ``System-V``
like init system (including ``upstart``) or the more modern ``systemd``, you will
need to follow different instructions. Please note that ``systemd`` is the
default in recent versions of Debian and RedHat-based systems.

.. toctree::
   :maxdepth: 1

   install_conf_daemon_sysv
   install_conf_daemon_systemd
