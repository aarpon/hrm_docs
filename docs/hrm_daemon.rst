.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

.. _`hrm_daemon`:

***********************
Install the hrmd daemon
***********************

|ubuntu| Ubuntu
===============

Use the ``$BIN/hrmd`` daemon in Ubuntu Linux to start the queue manager. The configuration file for the hrmd daemon is ``/etc/hrm.conf`` (see :ref:`hrm_conf`)

Start at boot
-------------

To start the queue manager at boot, copy ``$BIN/hrmd`` to ``/etc/init.d``. Make sure it is executable by typing (as root) in a shell:

.. code-block:: sh

    chmod +x /etc/init.d/hrmd

Then type:

.. code-block:: sh

    update-rc.d hrmd defaults

to install it in the default run-levels.

Start at manually
-----------------

Make sure to set the proper value of ``SUSER`` in ``/etc/hrm.conf`` (see :ref:`hrm_conf`).

Start a shell and type:

.. code-block:: sh

    sudo /etc/init.d/hrmd start

with a user that is allowed to sudo; otherwise:

.. code-block:: sh

    su -
    /etc/init.d/hrmd start

If the queue manager started correctly, you should see:

.. code-block:: sh

    Reporting to /var/log/hrm/log.txt /var/log/hrm/error_log.txt 
    Starting HRM daemon...................ok

The queue manager can be started, stopped and restarted by using:

.. code-block:: sh
    
    hrmd start
    hrmd stop
    hrmd restart.

|fedora| Fedora
===============

Coming soon.
