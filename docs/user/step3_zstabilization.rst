.. include:: global_directives.inc

.. _z_stabilization:

Stabilization in Z
=====================

This option will only be shown when restoring STED images (including STED 3D).
Due to the high lateral resolution in STED, image acquisition in more
sensitive to drift in STED than in other microscopy modes.

|ZStabilizationScreenshot|

.. note:: It is **strongly recommended** to select Z stabilization on STED
          images.

The stabilization is performed before deconvolution. This significantly
improves the restoration results.

Z stabilization is also recommended on STED 3D images although Huygens can
automatically skip it depending on the PSF shape of each particular case.
