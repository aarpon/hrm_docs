.. include:: global_directives.inc

.. _queue_status:

************
Queue status
************

After submitting a job HRM returns to the home panel. The Queue Status button
shows how many queued jobs you own, as follows:

|QueueStatusScreenshot|

Click on the button to get a detailed view of the job queue.

|QueuedJobsScreenshot|

HRM manages the deconvolution of multiple jobs owned by different users
through a smart queue. The job being processed is marked in green.

The **server** field will show the name of the machine and, when applicable,
the number of the GPU card processing the image. HRM can process multiple jobs
at the same time.

.. note:: The total number of processing machines and GPU cards defines the
          jobs than HRM can process in parallel.

To delete any of your jobs, select them in the queue table and click
|TrashBin22x22|.

.. note:: Depending on the HRM configuration settings, a notification email
          will be sent to the job owner when the job is finished. 

If the job's result seems wrong, try to verify if there is a mistake in the
settings. Contact the HRM administrator otherwise.

