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

|RegistrationLink| |RegistrationForm|


Upload a raw image
==================

Upon successful logging the HRM `Home panel` will be displayed:

|HomePanel|

To upload images click on the `Raw images` icon |RawImages22x22|. The
following, intuitive upload tool allows for multiple uploads from your local
device:

|UploadFiles|


Deconvolve
==========

To submit a deconvolution job proceed to `Start a job` |StartJob22x22| from
the home panel. The process of submitting the job is split into the following
5 steps:


* |SelectImages48x48| **Step 1/5 - Select images**: click on the "Image File
  Format" drop
  down  widget to select the desired file type for the images that you wish to
  deconvolve. All files of that format in your `"Raw Images"` folder will be
  listed. Use the |DownArrow22x22| |UpArrow22x22| icons to discard/include
  images from/into the selection. When selecting a file, a preview can be
  requested by using the link |GeneratePreviewLink| on the right panel. The
  image preview also provides information about the dimensions, sampling and
  number of channels.


* |ImageParameters48x48| **Step 2/5 - Image parameters**: An image parameter
  template
  matching the imaging conditions of the microscope can be created at this
  stage. Alternatively, an existing template can be selected from a
  previous run. Also, other HRM users (including the administrator) may have
  shared templates with you. Notice that choosing the correct parameters
  is **crucial** for obtaining optimal deconvolution results.

  **Use existing parameter template (easy)**: When selecting an existing
  parameter template the parameter contents are displayed on the right panel.
  Make sure that the  microscope type and the number of channels of the
  selected template match those of the images to deconvolve.

  **Create a new parameter template (elaborated)**: Type a name for the new
  parameter template in the `New/clone image template name` field, then click
  the create button |CreateTemplate22x22|. The template editor opens, select
  the correct
  number of channels and PSF type. Move on to the optical parameters and
  select the correct microscope type. For a detailed explanation on the
  remaining parameters please refer to section :ref:`advanced_deconvolution`.

* |RestorationParameters48x48| **Step 3/5 - Restoration parameters**:
  As in the previous step it's possible to choose between an existing template
  or creating a new one.
  
  **Use existing parameter template (easy)**: Select a parameter template
  and verify its contents on the preview shown on the right panel.
  Particularly, pay attention to the value
  of the Signal to Noise ratio (SNR) (see :ref:`signal_to_noise_ratio` for
  further help).
  
  **Create a new parameter template (elaborated)**:
  Follow the instructions of the previoius step to create a new template.
  Once in the template editor select a deconvolution algorithm (CMLE is 
  a good choice) and an SNR. Follow the instructions of the embedded SNR
  estimator for a hint on the SNR of your images. Set the background mode to
  automatic, the number of iterations to 40 and the quality change to 0.01.
  For more detailed fine-tuning follow the instructions at
  :ref:`advanced_deconvolution`.
  




  *(4/5)* *Analysis parameters* . This step is only available if you
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
