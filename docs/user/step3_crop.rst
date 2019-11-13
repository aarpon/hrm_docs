.. include:: global_directives.inc

.. _crop_image:

Crop image
==========

HRM can intelligently crop your images without losing important data. 

|CropScreenshot|

Select from:

* **Apply conservative crop**: to save computation time.

* **Do not crop the image**: if computation time is not an issue.

.. note:: The **time needed** to deconvolve an image increases more than
   proportionally with the **image volume**. Thus, cropping the image will
   speed up its restoration and the processing of the HRM queue.
