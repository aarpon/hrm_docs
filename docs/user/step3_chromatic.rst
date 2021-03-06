.. include:: global_directives.inc

.. _chromatic_aberration_correction:

Chromatic Aberration Correction
===============================

This option will only be shown when restoring multi channel images. In order
to let HRM know that an image batch contains multi channel images please set
the number of channels correctly, as explained in :ref:`number_channels`.
                                                        
The restoration template editor contains a section for post-deconvolution
operations. Options for these operations
(chromatic aberration correction and stabilization of time series) only show
up when applicable, i.e, multichannel images and time series. 

Therefore, the following section will only be displayed when restoring multi
channel images:

|ChromaticScreenshot|

Choose a reference channel:

|ChromaticScreenshot2|

The chromatic aberration can be described by an x-y-z shift + rotation +
scale (zoom) of each channel with respect to the reference channel.
Therefore, by definition the reference channel has no x-y-z shift, rotation
or scale. For the other channels, type in the shifts, rotations and scales.

|ChromaticScreenshot3|

The table will contain one entry per channel.

For an accurate estimation of the chromatic aberration 
one can use a local installation of Huygens Professional or Huygens Essential,
see `Chromatic Aberration Corrector <https://svi.nl/ChromaticAberrationCorrector>`_.

Use the estimated x-y-z shifts, rotations and scale values reported by
Huygens Professional or Essential to fill out the table. All images recorded
with the same settings and the same microscope can be corrected with the
same chromatic aberration values.

.. note:: For skipping this correction simply leave the table fields empty.
