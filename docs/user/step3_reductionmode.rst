.. include:: global_directives.inc

.. _reduction_mode:

Array Detector Reduction Mode
=====================

This option will only be shown when restoring Array Detector images
(Airyscan, SPAD, etc).
Array Detector images contain one acquisition per detector. The user can tell
Huygens how to combine the data from all the detectors for deconvolution. 

|ReductionModeScreenshot|

The following options are possible:

* **All**: the images from all detectors are centered and combined, thus
  increasing the SNR. The resulting, combined image is then deconvolved. 

* **No**: the independent detectors are not combined prior to deconvolution.
  They are used as separate inputs of a 'parallel' deconvolution. 

* **Core all**: Same as **All** but taking into account the central detectors
  only.

* **Core no**: Same as **No** but taking into account the central detectors
  only.

* **SuperY**: Create an image with 4 times as many samples in Y. This is mostly
  useful when dealing with images recorded with the Zeiss Airyscan in
  **fast mode**.

* **SuperXY**: Create an image with double the samples in X and Y. Thus,
  producing an image with 4 times more samples. This is a good option when
  dealing with images that have been acquired well under the Nyquist sampling
  rate.

* **Auto**: Automatic selection of one of the above mentioned modes depending on
  the microscopic parameters and detector model of the image.  


In all cases the SNR value specified in :ref:`signal_to_noise_ratio` is for
the central detector. Huygens will scale the SNR for the combined detectors
automatically.
