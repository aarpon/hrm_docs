.. include:: global_directives.inc

.. _step2:

The Image Parameters (2/5)
==========================

In step 2 - |ImageParameters22x22| **Image Parameters** - the microscope
settings can be specified and saved. The image parameters are grouped in
templates. A parameter template can be reused in future deconvolution jobs.
This will be useful when there are more images recorded under the same
conditions. Moreover, the parameter templates can be shared among HRM users,
fostering collaboration and re-usage of good image settings.


Notice that the following selections are possible at this stage:

* **Admin image templates**: parameter templates created by the HRM administrator to
  be used as references. They can be copied and edited by the HRM users. In
  order to use them, they first need to be copied to **Your image templates**
  by using |DownArrow22x22|.
   
* **Your image templates**: the image templates the user can actually use
  directly. All templates in this area may be selected, edited, removed, etc.

* **New/clone image template**: entry field for the name of a new parameter
  template. First type a name for the new template and click on
  |CreateTemplate22x22|. A new template will be created. HRM will present you
  with empty template parameters so that meaningful values can be assigned
  to them.


.. note:: Notice that |CreateTemplate22x22| |EditTemplate22x22|
          |CloneTemplate22x22| |ShareTemplate22x22| |FavouriteTemplate22x22|
          |DeleteTemplate22x22| show tooltips stating their action w.r.t
          templates. Namely, **create**, **edit**, **clone**, **share**,
          **mark as favourite** and **delete**.

An image parameter template consists of a number of relevant microscopic
parameters. These provide Huygens Core with information about the images
that will be deconvolved. To get a **preview** of the template contents select
the template, the contents will be displayed on the right panel.

.. note:: When editing a template help links |HelpLink22x22| are displayed at
          key locations to point you to specific articles of the SVI-wiki.

The following parameters can be edited in a template.
          
.. toctree::
   :maxdepth: 3

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
   step2_sphericalaberration
             
