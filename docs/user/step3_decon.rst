.. include:: global_directives.inc

Deconvolution algorithm
=======================

From HRM 3.7 onwards it is possible to select one deconvolution algorithm
per image channel. In most cases this will not be necessary and the user
will likely find it convenient to deconvolve all the image channels with
the same deconvolution algorithm.

For each channel choose one of the deconvolution algorithms from the
corresponding drop down widget.

|DeconAlgsScreenshot|

The available choices are:

* **Classic Maximum Likelihood Estimation (CMLE)**: CMLE is the method of
  choice under most circumstances. In case of doubt, CMLE should be used.

* **Quick Maximum Likelihood Estimation (QMLE)**: QMLE is faster than CMLE,
  but gives slightly less precise solutions in some cases. One may consider
  using QMLE in compute-intensive situations, for example, when deconvolving
  widefield 3D-time series.

* **Good's roughness Maximum Likelihood Estimation (GMLE)**: GMLE is a good
  alternative for high-noise images, such as STED or confocal.

* **Skip** : for not deconvolving this channel and keeping the raw data
  instead.



.. note:: Skip **all channels** of an image to use HRM as a pure batch file
   converter, chromatic aberration corrector, time stabilizer, colocalization
   analyzer, etc.
