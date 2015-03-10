.. include:: global_directives.inc
             

PSF Type
========

To perform image deconvolution a Point Spread Function (PSF) is needed.

The Huygens software can compute a **theoretical** PSF from the image parameters
used during deconvolution or it can use a **measured** PSF.

|PSFTypeScreenshot|

Depending on the user choice HRM will, at a later stage, ask for:

* the path to the file containing the PSF if you selected `Measured`,
* the settings to correct for spherical aberration if you selected
  `Theoretical` and there is a refractive index mismatch.

In most cases a theoretical PSF works fine.

