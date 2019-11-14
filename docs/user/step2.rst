.. include:: global_directives.inc

.. _step2:

The Image Parameters (2/5)
==========================

In step 2 - |ImageParameters22x22| **Image Parameters** - the microscope
settings can be specified and saved. The image parameters are grouped in
templates. A parameter template can be reused in future deconvolution jobs.
This will be useful when there are more images recorded under the same
conditions. Moreover, the parameter templates can be shared with one or more
HRM users.


The following selections are possible at this stage:

* **Admin image templates**: parameter templates created by the HRM
  administrator to be used as references. These templates cannot be changed
  directly. Instead, they can be copied to **Your image templates** (see below)
  for  further changes. For copying to **Your image templates** select the
  admin template and use |DownArrow22x22|.


|AdminTemplatesScreenshot|
   
* **Your image templates**: the image templates that the user can use
  directly. All templates in this area may be selected, edited, removed, etc.

|UserTemplatesScreenshot|

.. note:: |CreateTemplate22x22| |EditTemplate22x22| |CloneTemplate22x22|
          |FromImage22x22| |HuygensTemplate22x27|
          |ShareTemplate22x22| |FavouriteTemplate22x22|
          |DeleteTemplate22x22| show tooltips describing their actions w.r.t
          templates. Namely, **create**, **edit**, **clone**,
          **import from an image**, **import from a Huygens template**,
          **share**, **mark as favourite** and **delete**.

An image parameter template consists of several microscopic pararameters
relevant for deconvolution. To get a **preview** of the template contents select
the template, the contents will be displayed on the right panel.

|ParamPreviewScreenshot|

.. note:: When editing a template help links |HelpLink22x22| are displayed at
          key locations to point you to specific articles of the SVI-wiki.

The following parameters can be edited in a template.
          
.. toctree::
   :maxdepth: 1

   step2_numberchannels
   step2_psf
   step2_microscopetype
   step2_imagemetadata
   step2_na
   step2_wavelengths
   step2_objective
   step2_samplemedium
   step2_voxelsize
   step2_MeasuredPsf
   step2_pinhole
   step2_sted
   step2_spim
   step2_sphericalaberration
             
