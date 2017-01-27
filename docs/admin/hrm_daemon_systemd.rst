.. include:: global_directives.inc

.. _install_hrmd_systemd:

Install the HRM daemon as a systemd service
===========================================

If your Linux distribution is using the ``systemd`` init system, we recommend to
**not** using the "classical" init script (described in
:ref:`install_hrmd_sysv`). Instead, we are providing a unit file that can be
used with systemd directly.

.. warning::

    Please make sure to only follow **EITHER** the instructions given in this
    chapter here for installing the daemon on ``systemd`` based systems, **OR**
    the ones for ``System-V``/``upstart``, but **NEVER BOTH**.

    If unsure, or in case of problems with systemd, use the :ref:`instructions
    for System-V <install_hrmd_sysv>`!

Change the default configuration in the unit file
-------------------------------------------------

By default, the unit file is to configured to run as the ``hrm`` user and to depend on 
``mysql.service``. If needed, you can change those values before you proceed with the installation.

.. code-block:: sh

  [Unit]
  Description=HRM (Huygens Remote Manager) Queue Manager Service
  # For both 'Requires=' and 'After=', please set one of mysql.service, 
  # mariadb.service (fork of mysql), postgresql.service.
  Requires=mysql.service
  Wants=network-online.target
  After=mysql.service network.target network-online.target

  [Service]
  # If needed, change 'User=' and 'Group=' to point to the correct values.
  User=hrm
  Group=hrm
  ExecStart=/var/www/html/hrm/bin/hrm_queuemanager --detach
  Type=forking
  PIDFile=/var/log/hrm/hrmd.pid

  [Install]
  WantedBy=multi-user.target


Please change the values of ``Requires=``, ``After=`` to point to the correct database you are using for HRM
(one of ``mariadb.service``, ``mysql.service``, ``postgresql.service``) and ``User=`` and ``Group=`` if you are
planning to run the Queue Manager as a different user (please see also `set-up-the-hrm-user-and-group`).

Install the unit file
---------------------

To launch the HRM daemon as a systemd service, the unit file has to be copied
into ``/etc/systemd/system/`` and systemd has to be notified of the new unit.
This is done with these commands:

.. code-block:: sh

    sudo cp -v $HRM_RESRC/systemd/hrmd.service /etc/systemd/system/
    sudo systemctl daemon-reload

Start / stop the daemon at boot / shutdown
-------------------------------------------

To tell systemd to start the service at boot and stop it during shutdown, use
this command:

.. code-block:: sh

    sudo systemctl enable hrmd.service

Start / stop / check the HRM daemon manually
--------------------------------------------

To start the daemon manually, type in a shell:

.. code-block:: sh

    sudo systemctl start hrmd.service

Note that in case of a successful start, there will be no output. If the daemon
did not start correctly, systemd will produce a number of output lines telling
you about how to debug the problem.

To check if the queue manager daemon is running, use the ``status`` command.

.. code-block:: sh

    sudo systemctl status hrmd.service

In case the service is operational, it will show a message like this:

.. code-block:: sh

    * hrmd.service - HRM (Huygens Remote Manager) Queue Manager Service
       Loaded: loaded (/etc/systemd/system/hrmd.service; enabled; vendor preset: disabled)
       Active: active (running) since Thu 2016-02-11 15:05:22 CET; 18ms ago
      Process: 7782 ExecStart=/var/www/html/hrm/bin/hrm_queuemanager --detach (code=exited, status=0/SUCCESS)
     Main PID: 7785 (hrm_queuemanage)
       CGroup: /system.slice/hrmd.service
               |-7785 /bin/bash /var/www/html/hrm/bin/hrm_queuemanager
               |-7791 php -q /var/www/html/hrm/run/runHuygensRemoteManager.php
               `-7792 sleep 1


The queue manager can be started, stopped and restarted by using:

.. code-block:: sh

    sudo systemctl start hrmd.service
    sudo systemctl stop hrmd.service
    sudo systemctl restart hrmd.service
