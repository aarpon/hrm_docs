.. include:: global_directives.inc

.. _hot_pixel_correction:

Hot Pixel Correction
===============================

Hot Pixel Correction masks need to be created beforehand using Huygens
Professional or Essential and uploaded to the **Raw images** folder.

.. note:: Multichannel masks are supported.
          

When presented with the **Hot Pixel Correction file selection** window,

|HotPixelCorrection1|

browse for the mask of the camera used for the image acquisition.

|HotPixelCorrection2|

Select the Hot Pixel mask and click close.

Afterwards, press save and return to the image parameter selection page.

|HotPixelCorrection3|

The correction will only be applied to those images of the batch that have
the same XY dimensions as the mask.

.. note:: This correction is optional. The selection can be left empty.
	  Use the reset button to unselect a previously selected mask.
           
