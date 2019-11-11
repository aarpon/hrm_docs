.. include:: global_directives.inc

.. _signal_to_noise_ratio:

Signal to Noise ratio
=====================

In the Huygens Software the Signal-to-Noise ratio (SNR) is treated as a
regularization parameter, i.e., a means to control the sharpness of the
deconvolution result.


Yet, one should be aware of the effect of extreme SNR values on image
deconvolution: too high SNR values can produce restoration artifacts; too low
SNR values can lead to smooth structures.


.. note:: After a little practice it is possible to assess the SNR range for
          deconvolution visually. Notice that the SNR should increase with the
          quality of the raw data.
   

There are different acquisition settings that have an impact on the quality of
the recorded signal. Changing these in the experimental setup will most likely
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

As a guide, here the typical values for different microscopy tecniques:

* **Confocal**: between 20 and 40. 

* **STED**: between 10 and 20.

* **Widefield**: between 40 and 60. 

HRM offers an estimator to further help you find good SNR values for the
deconvolution runs. Click on |SNREstimatorLink| to use the **SNR estimator**.


In a new page you will be asked to select an SNR estimation method.

|SNRAlgorithmScreenshot|   

The **beta** method gets good estimations on images without a baseline. When
working with images that contain a baseline the **classic** method can be used
instead.



Next, select an image that represents the acquisition run of the batch that is
to be deconvolved in this job. Press |Calculator22x22| for the SNR estimation:


|SNREstimationScreenshot|

The output of the SNR estimator shows (per channel) a thumbnail next to 4
different noise simulations of the same region. In bold letters the SNR of the
simulation that most resembles the original image.


By pressing |Next22x22| the estimated SNR values are copied into the
restoration parameter template.

