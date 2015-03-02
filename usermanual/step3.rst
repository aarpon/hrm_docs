The Restoration Parameters (3/5)
================================

A set of restoration parameters instructs Huygens Core how to restore
your image. Some of these parameters are used before deconvolution, the
background correction, for example, subtracts a background value from
the image before deconvolution. Most options refer to the deconvolution
itself, for example the Signal to Noise Ratio (SNR), the number of
iterations (stopping criterium) or the convergence quality to a solution
(stopping criterium).

The background and the SNR are both linked to different important
acquisition parameters, changing these in the experimental setup will
most likely change the SNR and background of the recorded image,
requiring them to be reset in the restoration parameters set.

|image45|

-  Gain / offset
-  Time exposure / scanning velocity
-  Summing / averaging
-  Laser power
-  Spectral detection range

|image46|

The initial page of the Restoration Parameters (see `See Restoration
Parameter Step. At the end of this step a restoration parameter is
selected. On the right a summary of the selected set is
displayed. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_15031>`__)
resembles the Image Parameters page (See `See Image parameters, main
page. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_15842>`__). Thus,
templates made by the HRM administrator can be selected, copied, and
edited for customization. New parameter sets can also be created from
scratch.

|image47|

A Restoration Parameter set includes the following parameters (See `See
Restoration Parameter set: Deconvolution algorithm, SNR estimation,
background mode and stopping
criteria. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_53130>`__):

|image48|


.. toctree::
   :maxdepth: 3

   step3_decon
   step3_snr
   step3_background
   step3_stopcriteria
