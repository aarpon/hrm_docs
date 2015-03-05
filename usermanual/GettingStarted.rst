.. include:: global_directives.inc

***************
Getting started
***************

Here is a quick guide to get you started with the HRM/HuCore deconvolution. In
order to optimize results, please refer to section :ref:`advanced_deconvolution`.

Create an account in HRM
========================

-  If your imaging facility already offers deconvolution via HRM, proceed to
   the facility's HRM loging page.
   
-  If HRM is not available at your imaging facility you can still familiarize with
   HRM by using the `HRM demo server <http://hrm.svi.nl>`_ offered by
   SVI.

Follow the registration link on the HRM login page and complete the short
form. Notice that names are case sensitive. Upon registration the new HRM
account needs to be validated by the administrator.

   |image2| |image4|


Upload a raw image
==================

Upon successful logging The HRM `Home panel` will be displayed:

|image0|

To upload images click on the `Raw images` icon. The following, intuitive
upload tool allows for multiple uploads from your local device:

|image3|


Deconvolve
==========

To submit a deconvolution job proceed to `Start a job` |image5| from the home
panel. The process of submitting the job is split into the following 5 steps:


* |image6| **Step 1/5 - Select images**: click on the "Image File Format" drop
  down  widget to select the desired file type of the images that you wish to
  deconvolve. All files of that format in your `"Raw Images"` folder will be
  listed. Use the up/down arrow icons |image7| |image8| to discard/include
  images from/into the selection. When selecting a file, a preview can be
  requested by using |image9| on the right panel. The image preview provides
  information about the dimensions, sampling and number of channels.


* |image10| **Step 2/5 - Image parameters**: An image parameter template
  matching the imaging conditions of the microscope can be created at this
  stage. Alternatively, an existing template can be selected from a
  previous run. Also, other HRM users (including the administrator) may have
  shared templates with you. Notice that choosing the correct parameters
  is **crucial** for obtaining optimal deconvolution results  .

  **Use existing parameter template (easy)**: When selecting an existing
  parameter template the parameter contents are displayed on the right panel.
  Make sure that the  microscope type and the number of channels of the
  selected template match those of the images to deconvolve.

  **Create a new parameter set (elaborated)**: Type a name for the new
  parameter template in the `New/clone image template name` field, then click
  the create button |image11|. The template editor opens, select the correct
  number of channels and PSF type. Move on to the optical parameters and
  select the correct microscope type. For a detailed explanation on the
  remaining parameters please refer to section :ref:`advanced_deconvolution`.

* |image12| **Step 3/5 - Restoration parameters**: Choose the parameters that will
  communicate with Huygens how the image must be restored. *Use predefined
  (easy). Again a number of predefined sets from your administrator are
  available. It is worthwhile however to edit the set and obtain the
   appropriate SNR (see next). *Create your own (fairly easy).* Create or
   edit a set and enter the setup. For deconvolution algorithm choose
   Classic Maximum Likelihood
   Estimation.



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
