.. include:: global_directives.inc

***************
Getting started
***************

Here is a quick guide to get you started with the HRM/HuCore deconvolution. In
order to optimize results, please refer to section :ref:`advanced_deconvolution`.

Create an account in HRM
========================

-  If your imaging facility offers deconvolution via HRM, proceed to
   the facility's HRM loging page and follow the registration link.
   Notice that names are case sensitive.
   
   |image2|
   
-  If HRM is not available at your imaging facility you can still familiarize with
   HRM by using the `HRM demo server <http://hrm.svi.nl>`_ offered by
   SVI. Follow the registration link on the login page.


Upload a raw image
==================

Go to *raw images* and upload a file via the upload icon. Select a file
from your PC. Several files can be uploaded at once.

|image6|

Deconvolve
==========

From the main screen, go to *start a job* , entering the deconvolution
process.

|image7|

*(1/5)* *Select files.* First Select the desired file type, all files of
that format in the deconvolution directory will be listed. Use the up en
down icons to choose which files will be deconvolved. Multiple files can
be selected, if they have the same format. When selecting a file, a
preview can be generated on the right panel when requested. This preview
provides information about your image, including the dimensions,
sampling and the number of channels used.\ **

|image8|

*(2/5)* *Image parameters* . Select a parameter set, this parameter set
contains information about how the image was created. Choosing the
correct parameters is crucial for obtaining good deconvolution results.

*Use predefined (easy)* . There are a number of predefined deconvolution
formats by your administrator. Make sure that the microscope type and
the correct number of channels is selected (visible in the preview on
the previous page). Proceed to the next step.

|image9|

*Create your own (harder)* . Depending on the file format, some
parameters are already provided by the metadata. HRM will inform whether
usable metadata is present. To use the parameters in the metadata, leave
the field blank. For advanced users it is possible to tune and tweak
their parameters to optimize results, this is explained in `See Advanced
deconvolution in HRM <HRMUserManual.htm#50532397_51687>`__.

First create a new set, by entering a set name and press the new
parameter set icon. Alternatively, it is possible to edit an existing
set.

The new parameter set opens, select the correct number of channels
(visible in the preview in the first step *(1/5)* ). And select
theoretical PSF.

Next are the optical parameters. You need to know the parameters of your
experiment and enter them, some of these may be included in the metadata
as illustrated in `See The first optical parameters page. Shown is which
parameters must be provided and which may be
0mitted <HRM/HRM%20Introduction.htm#50532372_47906>`__. Note that there
are two pages of optical data. There are several calculators available
to help you enter the correct data. Additionally, it is possible to
calculate the pixel size by dividing the size of the image by the number
of pixels in that dimension, which are both shown in the preview of the
first step *(1/5)* .

|image10|

Finally select whether you want to enable depth-dependent correction of
the PSF. NO is default. YES improves the image quality, but also takes
slightly longer to calculate. Here it is additionally necessary to
submit from which side of the image the measurement started.

*(3/5)* *Restoration parameters* . Choose the parameters that will
communicate with Huygens how the image must be restored.

*Use predefined (easy).* Again a number of predefined sets from your
administrator are available. It is worthwhile however to edit the set
and obtain the appropriate SNR (see next).

*Create your own (fairly easy).* Create or edit a set and enter the
setup.

-  For deconvolution algorithm choose Classic Maximum Likelihood
   Estimation.

|image11|

-  Now use the SNR calculator. Upon entering an image, the calculator
   shows estimated previews of restored images for different SNR, along
   with recommendations by the software, as seen in `See The SNR
   estimator. Image is courtesy of Anko de Graaff from the Hubrecht
   Institute. <HRM/HRM%20Introduction.htm#50532372_80119>`__. Pressing
   forward means accepting the recommendations. Note that for each
   channel an SNR must be chosen. This SNR is used for the entire set of
   images, selected in step *(1/5)* . If one image has less channels
   than submitted, only the first are used. As a guideline, use 20 for
   confocal microscopy and 40 for widefield microscopy.

|image12|

-  Background mode. Choose automatic background estimation.
-  Stopping criteria. The deconvolution will stop when either of two
   criteria are met. 20 iterations and a quality change of 0.05 are good
   default values.
-  *(4/5)* *Analysis parameters* . This step is only available if you
   have a coloc license and if there is more than one channel available
   for colocalization. Choose which analysis to perform on the image.
   The colocalization\ `6 <#50532361_pgfId-949465>`__ analyzer is
   already available on HRM and more options and tools will follow.

*Use predefined (easy)* . Again there are a number of predefined
options, choose whether you want colocalization or not.

*Create your own (medium)* . Create or edit your own set. First choose
whether you want Huygens to do a colocalization calculation. If you do,
choose for which channels you want colocalization (default all
channels). Next choose your colocalization coefficients, thresholds and
map. As default select all the colocalization coefficients, choose
automatic estimation for the threshold and Pearson for your
colocalization map.

|image13|

*(5/5)* *Launch* . Check whether all the configurations are correct and
choose an output format. SVI-HDF5 is well suited for the Huygens
environment and is very good at carrying metadata and compressing file
data. ICS is a good allrounder. To deconvolve press the big green button
at the bottom of the page.

|image14|

Queue
=====

The job is now placed in the queue. HRM has a smart queue, which manages
the jobs of several different users in an intelligent way. Allowing
small jobs to go in between large ones. Here jobs of all users can be
viewed and own jobs can be deleted.

|image15|

Results
=======

After deconvolution the images are placed in the results folder,
accessible via the main menu. From there, files can be downloaded or
viewed from the server.\ *
* Click on *detailed results* in the right window to preview and compare
the deconvolution result with the original image, illustrated in `See
Compare deconvolved results using the MIP renderer. Image courtesy of
Anko de Graaff. <HRM/HRM%20Introduction.htm#50532372_11946>`__.

|image16|

|image17|

Tips & Tricks
=============

To optimize your deconvolution results it is necessary to understand the
different properties of your image and some of the mechanisms behind
deconvolution. If you’ve followed this guide, many properties have been
assigned default values. We would like to encourage the users to read
into and explore different settings, which will help you improve your
deconvolution results. Some more in-depth knowledge is given in chapter
`See Advanced deconvolution in
HRM <HRMUserManual.htm#50532397_51687>`__.
