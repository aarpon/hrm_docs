.. include:: global_directives.inc

.. _signal_to_noise_ratio:

Signal to Noise ratio
=====================

In the Huygens Software the Signal-to-Noise ratio (SNR) is treated as a
regularization parameter, i.e., a means to control the sharpness of the
deconvolution result.


Yet, please be aware of the effect of extreme SNR values on image
deconvolution: too high SNR values can produce restoration artifacts; too low
SNR values can lead to smooth structures.


.. note:: After a little practice it is possible to assess the SNR range for
          deconvolution visually. In general, the SNR should increase with the
          quality and amount of signal of the raw data.
   

There are different acquisition settings that have an impact on the quality of
the recorded signal. Changing these in the acquisition system will most likely
require a modification of the SNR value for deconvolution. These acquisition
settings are:


*  Gain / offset
*  Time exposure / scanning velocity
*  Summing / averaging
*  Laser power
*  Spectral detection range

Because these settings are typically different for each channel HRM will
require an SNR value per channel, like this:


|SNRScreenshot|

As a guide, these are typical SNR values for different microscopy tecniques:

* **Confocal**: between 20 and 40. 

* **STED**: between 10 and 20.

* **Widefield**: between 40 and 60. 

HRM offers an automatic SNR estimator to determine suitable SNR values for
the raw images. Click on |SNREstimatorLink| to use the **SNR estimator**.


In a new page you will be asked to select an SNR estimation method.

|SNRAlgorithmScreenshot|   

The **Auto** method gets good estimations on images without a baseline. When
working with images that contain a baseline the **Legacy** method can be used
instead.


Next, select an image representative of the batch selected in :ref:`step1`.
Press |Calculator22x22| for the SNR estimation:


|SNREstimationScreenshot|

The output of the SNR estimator shows a region of the original data next to 4
different noise simulations of the same region. In bold letters the SNR of the
simulation that most resembles the original image.


By pressing |Next22x22| the estimated SNR values are copied into the
restoration parameter template.

