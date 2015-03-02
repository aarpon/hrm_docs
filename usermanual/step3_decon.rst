Deconvolution algorithm
=======================

Two deconvolution algorithms are available to process the data. The
Classic Maximum Likelihood Estimation (CMLE) algorithm and the Quick
Maximum Likelihood Estimation (QMLE) (See `See Restoration Parameter
set: Deconvolution algorithm, SNR estimation, background mode and
stopping
criteria. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_53130>`__).

The “Classic” algorithm should be used in most circumstances. The
“Quick” algorithm is faster, but gives less precise solutions in some
cases. One may consider using the “Quick” algorithm in compute-intensive
situations, for example, when deconvolving 3D-time series.
