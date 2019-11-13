.. include:: global_directives.inc

.. _background:


Background mode
===============

The background intensity is a nearly constant value that is present everywhere
in the image. 

|BackgroundScreenshot|

Three options are available for background correction. These options can
return slightly different values, therefore this choice can affect the
deconvolution result:

* **Automatic background estimation**: This estimation usually works well. The
  background is estimated within a region with a low mean value.

* **In/near object**: The background is estimated around intensity peaks. This
  option can be interesting, for example, when having bright little objects in a
  cell with a strong cytoplasmic background.

* **Remove constant absolute value**: To make sure that the same background
  level is removed from all the images in the batch, insert manually a measured
  mean background for each channel. This option is typically useful for those
  interested in doing fluorescence quantification or stitching.
