.. include:: global_directives.inc

.. _configure_multi:

********************************
Configure the HRM (multi-server)
********************************

This section describes the specific steps required to configure the HRM to run on multiple machines. In particular, we address the following setup:

    - **Machine 1**: runs the web server (and database) and the queue manager
    - **Machine 2**: runs Huygens Core
    - The data folder is not directly shared (via NFS or Samba) between the two machines.

.. note::

    There could be more than on processing machine running Huygens Core in your institution: set up all additional machines like **Machine 2**.

Configuration steps
===================

Public-key authentication
-------------------------

Image data for deconvolution is transferred from **Machine 1** to **Machine 2** via secure copy (``scp``). For this, a specified user on **Machine 2** must be created/chosen, and remote access from **Machine 1** via password-less, public key authentication must be set up for this user.

.. note::

    For the sake of the example, we will call this specific user ``hrm``. You can pick another user, just make sure to replace ``hrm`` with your user name in what follows.

On **Machine 2**, create a user with name ``hrm`` and group ``hrm`` that will be used for remote authentication and data transfer. Configure password-less, public key authentication as explained on this page_. The public key is uploaded to **Machine 2**, whereas the private key is stored on **Machine 1** for the selected user (e.g. in ``/home/hrm/.ssh/``).

.. _page: https://help.ubuntu.com/community/SSH/OpenSSH/Keys

HRM configuration files
-----------------------

On **Machine 1**, configure the HRM as usual (as in the single-server configuration) but set the following variables in ``$HRM_CONFIG/hrm_client_config.inc`` and ``$HRM_CONFIG/hrm_server_config.inc`` as shown:

.. code-block:: php

   <?php
   ...
   $copy_images_to_huygens_server = true;
   $imageProcessingIsOnQueueManager = false;
   $huygens_user = "hrm"   // This is the user that will log in to Machine 2
   $huygens_group = "hrm"  // And this is its group

Replace ``hrm`` with your own user name and group if different.

Processing servers
------------------

Log on to HRM as admin and go to `Servers and GPUs` |ServersGPUs22x22|.
Register the processing servers in HRM by adding an entry for every processing
machine, specifiying the absolute Huygens Core path on that machine, as well
as the machine name.

GPUs
----

The `Servers and GPUs` |ServersGPUs22x22| form allows you to also register GPUs in HRM for
further parallelization of the HRM processing queue.

To register a machine with no GPU cards then any GPU ID will do in the form. Use, for example, GPU ID = 0.

To register a machine with one or more GPU cards simply add different entries
for the GPUs of the same machine. As follows,

|ServersGPUsScreenshot|

HRM will consider each GPU card as a separate server. The HRM queue will
process as many images in parallel as the total number of registered GPU cards.

The GPU IDs can be retrieved with the NVIDIA tools or via HuCore. For example,
the following machine reports 2 GPUs with IDs 0 (Titan X) and 1 (Quadro P5000):

.. code-block:: sh

   > hucore
   % huOpt gpu -query names
       {0: TITAN X (Pascal)} {1: Quadro P5000} 

Data folder
-----------

On **Machine 2**, create the data folder pointed at by ``$huygens_server_image_folder``. This folder should be owned by ``$huygens_user`` (e.g. "hrm") and have group ownership as set by ``$huygens_group`` (e.g. "hrm").
