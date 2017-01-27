.. include:: global_directives.inc

.. _enable_gpus:

*************
Enable GPUs
*************


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
