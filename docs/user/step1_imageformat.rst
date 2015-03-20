Image format
============

The format of the image file is directly linked to the acquisition
system of the microscope (LEICA, ZEISS, Tiff series, etc).

Both HRM and the underlying engine, Huygens Core, use naming standards
such as the LEICA standard. When handling exotic tiff file names, such
as the tiff exports from PerkinElmer UltraView, it is recommended to
rename the files before proceeding with the deconvolution jobs. There
are freeware tools available to systematically change names of large
file groups\ `8 <#50532361_pgfId-989314>`__.

A few examples of different tiff standards include:

-  *Olympus FluoView* (\*.tiff): This is a particular tiff format (FM
   multi-layer) that can store multiple 2D planes in a 3D stack (single
   file).
-  *Leica series* (\*.tiff): Series of 2D images, with Leica Standard
   naming. Below, two examples of this standard:
-  XYZ-time, single channel: name\_t00\_z000.tif.
-  XYZ-time, multiple channels: name\_t00\_z000\_ch00.tif.
-  *Generic Tiff* (\*.tiff): Sequentially numbered series of 2D tiff
   images. Upload a single 2D image. When the *automatically load file
   series if supported* box is checked, all files from the series will
   be uploaded creating a 3D (time) series.

When all the files are selected, click on the *big right arrow* at the
bottom of the page to continue to the image parameter step.

