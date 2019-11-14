.. include:: global_directives.inc

.. _voxel_size:

   
Voxel Size
==========

The voxel size or sampling size is a very **important** parameter in image
deconvolution.

.. note:: According to the **Nyquist criterion** its value should not be
          larger than half the optical resolution of the imaging system.

HRM offers several utilities to help you set up this parameter correctly.

|VoxelSizeScreenshot|
          
Ideally, the optimal voxel sizes are calculated before acquiring the images.
By doing so, one can ensure that the images are compliant with the Nyquist
criterion. Click on |NyquistCalculatorLink| to determine how large the
voxel sizes should be. By using these values, there will be **no lost
information** during the image acquisition and the deconvolution will be able
to restore the original signal better.

If the optimal voxel sizes have not been determined before the acquisition
stage one can calculate the resulting sizes in **widefield** and
**spinning disk** microscopy by using |CCDCalculatorLink|. Here the voxel
sizes are calculated from the CCD camera element, the objective
magnification, etc., although no optimal voxel size can be guaranteed.
      
.. note:: Make sure to set a voxel size consistent with the Nyquist criterion.
          Undersampled images will often show artifacts after deconvolution.    

Lastly, for deconvolving time series set the time interval between subsequent
frames.

|TimeIntervalScreenshot|

Among other things, this will help HRM to decide when to stabilize the image.
