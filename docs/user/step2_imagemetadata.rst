.. include:: global_directives.inc

.. _image_metadata:

Import metadata
===============


Some parameters are always present in the meta data of specific file formats
and can be imported from the image at run time, while deconvolving the image,
to save you time. 

.. note:: When a parameter is **missing** from the meta data HRM needs input
          from the user. This is highlighted by a message like this:
          |MetadataScreenshot3| 
          
.. note:: When a parameter is **present** in the meta data HRM can work without
          the input from the user. This is indicated with |MetadataScreenshot2|

At the end of the deconvolution job, HRM informs on the values of all used
parameters as well as their origin (user input or meta data).
