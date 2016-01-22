.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. _`hrm_daemon`:

**********************
Install the HRM daemon
**********************

The HRM daemon consists of two parts, the actual queue manager (a PHP process)
and a shell-based wrapper in ``$HRM_BIN/hrm_queuemanager`` that prepares the
environment, checks the config, launches the queue manager and cleans up after
the process has terminated.

The configuration file for the HRM daemon is ``/etc/hrm.conf`` (see
:ref:`hrm_conf`)

.. warning::

    You should never start the PHP process directly as unpredicted effects will
    happen, in worst case including damage to the HRM database.

Install the init script
-----------------------

To launch the HRM daemon at boot, we are providing an init script in
``$HRM_RESRC/hrmd_lsb-init`` which can be placed in ``/etc/init.d/``. The
script makes use of the LSB init functions and therefore requires
``/lib/lsb/init-functions`` to be available in your distribution (which is true
for Ubuntu and Fedora, as well as most other major up-to-date Linux
distributions).

For installing the init script, type the following commands in a shell:

.. code-block:: sh

    sudo cp -v $HRM_RESRC/hrmd_lsb-init /etc/init.d/hrmd
    sudo chmod +x /etc/init.d/hrmd

Start / stop the daemon at boot / shutdown
--------------------------------------------

|ubuntu| Ubuntu: To set up the appropriate run-level links for starting and
stopping the daemon during boot and shutdown, use this command:

.. code-block:: sh

    sudo update-rc.d hrmd defaults

This will configure your system to run the init script in the default
run-levels. Please note that issuing this command does *NOT* actually start the
daemon until the next reboot. To start it right now follow the steps in the
section below.

|fedora| Fedora: *Coming soon.*

Start manually
--------------

Make sure to set the proper value of ``SUSER`` in ``/etc/hrm.conf`` (see :ref:`hrm_conf`).

Start a shell and type:

.. code-block:: sh

    sudo /etc/init.d/hrmd start

If the queue manager started correctly, you should see:

.. code-block:: sh

    Forking background process...
    Reporting stdout to '/var/log/hrm/log.txt' and stderr to '/var/log/hrm/error_log.txt'.

To check if the queue manager daemon is running, use the ``status`` argument.
In case the service is operational, it will show a message like this:

.. code-block:: sh

    [ ok ] HRM is running (/var/www/hrm/bin/hrm_queuemanager), PID: 1234.

The queue manager can be started, stopped and restarted by using:

.. code-block:: sh
    
    sudo /etc/init.d/hrmd start
    sudo /etc/init.d/hrmd stop
    sudo /etc/init.d/hrmd restart
