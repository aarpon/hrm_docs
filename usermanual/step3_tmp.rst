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







 and overal defines the how much of these fluctuations  should be corrected for of noise correction that deconvolution should perform. The SNR value should be a measure of hte noise of the original image.  
 The SNR
parameter defines the degree of noise correction that will be performed
and should be a measure of the noise of the original image. The user can
assess which SNR value is best or let HRM estimate it automatically.

For an automatic estimation click on *Estimate SNR from image* . Then,
select an image (see `See Select a method and image to estimate SNR. A
preview is shown on the right. Image courtesy of Drs. Jeff
Tucker. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_68128>`__) and
click on the *calculate* button, the SNR will be estimated for each
channel of the selected image.



The SNR estimation will be shown along with four noise simulations with
different SNR values. The noise simulations serve to confirm visually
the correctness of the automatic SNR estimation. Move the mouse pointer
over the different images to see them zoomed in.



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
