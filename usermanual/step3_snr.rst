.. _signal_to_noise_ratio:

Signal to Noise ratio estimation
================================

Noise are random fluctuations in the intensity of your image. The
deconvolution process may in general increase the noise of the original
images, as it restores the high frequencies. For this reason Huygens
will correct for noise during the deconvolution process. The SNR
parameter defines the degree of noise correction that will be performed
and should be a measure of the noise of the original image. The user can
assess which SNR value is best or let HRM estimate it automatically.

For an automatic estimation click on *Estimate SNR from image* . Then,
select an image (see `See Select a method and image to estimate SNR. A
preview is shown on the right. Image courtesy of Drs. Jeff
Tucker. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_68128>`__) and
click on the *calculate* button, the SNR will be estimated for each
channel of the selected image.

|image49|

The SNR estimation will be shown along with four noise simulations with
different SNR values. The noise simulations serve to confirm visually
the correctness of the automatic SNR estimation. Move the mouse pointer
over the different images to see them zoomed in.

|image50|

All images deconvolved with the same restoration parameter set should
have similar Signal to Noise Ratios. This will be the case if the images
have been taken with the same Gain, Offset, laser power and image
averaging for confocal imaging and the same Gain and time exposure for
widefield imaging. Each time these microscope settings are changed or a
different preparation is used the Signal to Noise Ratio should be
re-estimated.

The SNR is a delicate parameter as it can highly influence the
deconvolution result. On the one hand, if the deconvolution result looks
too smooth and details are missing, a higher SNR value can be used. On
the other hand, if the result looks too grainy one can try to use a
lower SNR value.

Since HRM 2.0.0 there exists a new Beta SNR estimator that aims at
improving the accuracy of the classic SNR estimator. Both tools are
currently available to estimate the SNR, though the Beta SNR estimator
is being tested and improved. Its estimations in Widefield images and
Confocal images free of baseline (black level) may already be accurate.
The Beta SNR estimator may not yet find accurate results in confocal
images that have a baseline or images that show strong clipping on the
lower side of the intensity range.
