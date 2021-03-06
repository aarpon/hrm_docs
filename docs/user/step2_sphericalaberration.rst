.. include:: global_directives.inc


Spherical Aberration correction
===============================

Spherical aberration is mainly caused by a **mismatch** between the refractive
indexes of the objective immersion medium and the sample embedding medium.

HRM will automatically detect this mismatch and ask whether the aberration
should be corrected for when using a theoretical PSF.

.. note:: Spherical aberration can be corrected for by creating different
          theoretical PSFs (with slightly changing shapes) at different
          depths: **depth-dependent PSF**.
          
|DepthDependentPSFScreenshot|

When using a depth-dependent PSF one also needs to specify whether the first
plane in the dataset is closest or farthest to/from the coverslip.

|DataOrientationScreenshot|

The **Correction mode** allows for a more detailed choice as to how the 
depth-dependent PSF should vary with depth.

|SACorrectionModeScreenshot|

* **Automatic correction**: will generate a depth-dependent PSF where
  the PSF is automatically selected at each depth, as explained above.
* **Advanced correction**: allows to specify further details about the
  depth-dependent PSF.

The `Advanced correction` will further enable a number of advanced options.

|SAAdvancedScreenshot|

* **Depth-dependent PSF on few bricks**: a different PSF will be generated
  for each Z brick in which the original data is split.
* **Depth-dependent PSF slice by slice**: a different PSF will be generated
  for each slice.
* **Depth-dependent PSF on few slabs**: several PSFs will be generated
  for each Z brick. This option is memory-consuming but the best choice when
  the spherical aberration is very strong. 


.. note:: Splitting the original data into bricks while
          deconvolving not only helps to correct for spherical aberration
          but it also **minimizes the amount of RAM memory**
          needed for deconvolution.
