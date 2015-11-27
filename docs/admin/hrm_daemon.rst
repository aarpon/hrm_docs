.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

.. _`hrm_daemon`:

***********************
Install the hrmd daemon
***********************

Use the ``$HRM_BIN/hrmd`` daemon in Ubuntu Linux to start the queue manager. The configuration file for the hrmd daemon is ``/etc/hrm.conf`` (see :ref:`hrm_conf`)

Install the init script
-----------------------

To start the queue manager at boot, copy ``$HRM_BIN/hrmd`` to ``/etc/init.d/``. Make sure it is executable by typing in a shell:

.. code-block:: sh

    sudo cp -v $HRM_BIN/hrmd /etc/init.d/hrmd
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

    Reporting to /var/log/hrm/log.txt /var/log/hrm/error_log.txt 
    Starting HRM daemon...................ok

The queue manager can be started, stopped and restarted by using:

.. code-block:: sh
    
    sudo /etc/init.d/hrmd start
    sudo /etc/init.d/hrmd stop
    sudo /etc/init.d/hrmd restart
