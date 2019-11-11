.. include:: global_directives.inc

             
Pinhole Radius
==============

Pinholes are used in  **confocal**, **spinning disk**, **STED**,
**STED 3D** and Rescan microscopy to get rid of out-of-focus light.
Since there's no pinhole in **widefield**, **two photon**  and SPIM
microscopes HRM skips this parameter in those cases.

|PinholeRadiusScreenshot|

.. note:: HRM needs the value of the pinhole **backprojected** on
          the specimen.

Further help on how to calculate the backprojected pinhole radius can be found
on |PinholeCalculatorLink|.


Pinhole Spacing
===============

**Spinning disk** microscopy uses more than one pinhole to speed up image
acquisition. The **backprojected** distance between these pinholes also
plays a role in image deconvolution. HRM skips this parameter for all
other microscope types.

|PinholeSpacingScreenshot|

Click on |PinholeCalculatorLink| for further help on the calculation of the
backprojected value.
