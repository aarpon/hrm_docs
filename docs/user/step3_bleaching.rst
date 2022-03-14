.. include:: global_directives.inc

.. _bleaching_correction:

Bleaching Correction
====================

Huygens can automatically estimate the amount of bleaching in the image and correct for it. This type of correction is mostly necessary for 2 types of images:

- Images from widefield-like systems. Since the specimen is exposed to large
  amounts of light it can be easily bleached.

- Time series from any type of microscope. Depending on how long the time
  series is the specimen can also be exposed to large amounts of excitation
  light.

.. note:: 2D/3D images froms confocal-like systems (no time series) don't need
	  to be corrected for bleaching.
          

When presented with the **Bleaching correction** option, it is recommended
to select 

|BleachingCorrection1|

for any time series and/or widefield-like images. 


Select

|BleachingCorrection2|

for all of the other images.


           
