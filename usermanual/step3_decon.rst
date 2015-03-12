.. include:: global_directives.inc

Deconvolution algorithm
=======================

Choose one of the deconvolution algorithms from the drop down widget.

|DeconAlgsScreenshot|

At the moment HRM offers two algorithms for the restoration of the images. 

* **Classic Maximum Likelihood Estimation (CMLE)**: CMLE is the method of choice under most circumstances. In case of doubt, CMLE should be used.

* **Quick Maximum Likelihood Estimation (QMLE)**: QMLE is faster than CMLE, but gives slightly less precise solutions in some cases. One may consider using QMLE in compute-intensive situations, for example, when deconvolving widefield 3D-time series.
