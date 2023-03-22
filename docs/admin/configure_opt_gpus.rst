.. include:: global_directives.inc

*************
Enable GPUs
*************

Graphics processors significantly reduce computing time (see `SVI page on GPU's <https://svi.nl/HuygensGPU>`_).

Configuration
=============

Log on to HRM as admin and go to `Servers and GPUs` |ServersGPUs22x22|.
The form in `Servers and GPUs` allows you to register GPUs (as well as other
processing servers) in HRM for further parallelization of the HRM processing
queue.

To add a new entry, enter the machine name and the absolute path of HuCore on
that machine.

To register a machine with no GPU cards enter a negative integer for the GPU ID.
Use, for example, GPU ID = -1.

To register a machine with one or more GPU cards simply add different entries,
one per GPU. All these entries should have the same Server Name and HuCore
Path, but different GPU IDs. As follows,

|ServersGPUsScreenshot|

HRM will consider each GPU card as a separate server. The HRM queue will
process as many images in parallel as the total number of registered GPU cards.

The GPU IDs can be retrieved via HuCore. For example,
the following machine reports 2 GPUs with ID 0 (Titan X) and ID 1 (Quadro P5000):

.. code-block:: sh

   > hucore
   % huOpt gpu -query names
       {0: TITAN X (Pascal)} {1: Quadro P5000} 


Performance considerations
==========================

Every time Huygens is launched NVIDIA checks to compile some Huygens code for
each of the GPUs in the system. This can easily take about 20 or more
seconds. Whenever possible NVIDIA caches the compilation results to avoid
repeating this time-consuming process. Thus, in practice, if the cache works
properly, new compilations only occur once, when a new NVIDIA driver is
installed. That one time Huygens shows the message ‘Slow GPU initialization …’
while launching.

As it turns out the NVIDIA cache is user-dependent and is located in the ‘.nv’
folder of the user running the process. Therefore, it is important that the
home folders of the 2 HRM system users (‘hrm’ and ‘apache’) have the proper
ownership, so that this cache can be created. Otherwise, **every single HRM job
will incur in a significant performance penalty**.

Thus, simply make sure the 2 following folders and ownerships are set
properly:

* Frontend machine:

.. code-block:: sh
   
   # www-data in Ubuntu, apache in |RHEL|
   sudo chown -R www-data:www-data /var/www

.. code-block:: sh

   Add 'export HOME=/var/www' after 'unset HOME' to '/etc/apache2/envvars'.

   Restart Apache.

                
* Processing machine(s):

.. code-block:: sh

   sudo mkdir -p /home/hrm
   sudo chown -R hrm:hrm /home/hrm


As a reminder, also notice that each HRM job has a corresponding Huygens log in the HRM ‘Detailed view’. If the system is properly configured then the message ‘Slow GPU initialization’ should not be logged.

