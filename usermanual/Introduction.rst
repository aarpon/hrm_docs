**************************
Introduction
**************************


What is HRM
===========

Welcome to the user guide for the Huygens Remote Manager (HRM)! HRM is a
web-based collaborative open-source interface to Huygens Core to do
multiuser, scheduled, batch deconvolution.

With a Huygens Remote Manager, it is possible for a large group of users
to work with Huygens on a central system through an easy interface.
Allowing for central administration in a cluster. It is web-based and
therefore easily accessible from many places. It can be accessed from
your workstation, home PC or tablet.

An HRM server can distribute work among several computers smartly, which
allows for intelligent use of calculation hardware and fast calculation
times. It combines flexibility in hardware choices with an intelligent
queue, allowing small jobs to go in between large ones.

|image0|

Who makes HRM
=============

HRM is an open source project, this means that the code is freely
accessible and it can be adapted and modified to any needs by any user.
It is developed by Huygens users at the Montpellier Rio Imaging
facility, the Facility for Advanced Imaging and Microscopy at the
Friedrich Miescher Institute (FMI, Basel), the BioImaging and Optics
Platform at the Ecole Polytechnique Fédérale de Lausanne and the
Department of Biosystems Science and Engineering at the ETH Zürich.
Scientific Volume Imaging participates in this project by contributing
its experience in deconvolution and software engineering. HRM is a free
and open source.

|image2|

Where to find HRM
=================

HRM is a free and open source project, and can be found in SourceForge
`1 <#50532361_pgfId-924454>`__.

More information about HRM and links to other HRM resources can be found
in the HRM online article of the SVI
Wiki\ `2 <#50532361_pgfId-924459>`__. Instructions for online testing,
downloading and installing HRM are also linked on that page.

Installing HRM on a running regular web server is very difficult. Apart
from the installation instructions that come along with the source code,
other practical guidelines can be found in the project’s official
site\ `3 <#50532361_pgfId-943475>`__ and in the SVI Wiki
`4 <#50532361_pgfId-922732>`__.

|image3|

Getting started
===============

Here is a quick guide to get you started with deconvolution. To optimize
results, please refer to `See Advanced deconvolution in
HRM <HRMUserManual.htm#50532397_51687>`__.

Create an account
=================

|image4|

-  If your imaging facility already has an HRM server, go to the server
   and create an account. Names are case sensitive. Contact your system
   administrator for activation.
-  If you don’t have an HRM system running, it is still possible to get
   familiar with Huygens by creating an account on the HRM demo
   server\ `5 <#50532361_pgfId-948297>`__ at SVI, as seen in `See The
   registration page for the HRM demo
   server. <HRM/HRM%20Introduction.htm#50532372_48684>`__

|image5|

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
