.. include:: global_directives.inc

.. _lauch_deconvolution:


************
Launch a job
************

To start a new job with deconvolution, chromatic aberration, stabilization, or
colocalization analysis click on `Launch jobs` |StartJob22x22| in the home
panel.
This page describes the general workflow which is split into the following **five** main steps.
The detailed description of all the parameters included by the templates used in this workflow is
documented on the following sub-pages:

.. toctree::
    :maxdepth: 1

    decon_job_image_template
    decon_job_restoration_template
    decon_job_analysis_template


.. _decon_job_step1:

Select images (1/5)
===================

In step 1 - |SelectImages22x22| **Select Images** - the user can add images
for deconvolution. A batch of images with the same properties can be selected
with Ctrl+click or Shift+click and added in one go.

|SelectImagesScreenshot|

Select the file format from the drop down widget and use
|DownArrow22x22| |UpArrow22x22| to add images to the **Selected images** area.

.. note:: The images of a batch must share the **same
          microscopic parameters** in order to obtain good deconvolution
          results because they will be restored with the same settings.
          This is generally true if the images are recorded with
          the same setup.

When an image is selected a preview is displayed on the right panel
whenever possible. If not yet available, a button shows up
|GeneratePreviewLink| to generate the preview on the fly.

.. note:: Image previews also display the image dimensions, number of channels,
   and sampling sizes in the overlay.

By default no particular image format is preselected and HRM shows all images
available in the user's raw images folder. Select a file format to filter out
images from other file extensions.


.. _decon_job_step2:

The Image Parameters (2/5)
==========================

In step 2 - |ImageParameters22x22| :ref:`Image Parameter<image_template>` - the microscope
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

New templates can be added to the list by creating them from scratch using the |CreateTemplate22x22| button,
by using the image metadata |FromImage22x22|, by importing a shared template |ShareTemplate22x22|, or by modifying
an existing template |CloneTemplate22x22|.
To modify a template simply click on the |EditTemplate22x22| button.

.. note:: |CreateTemplate22x22| |EditTemplate22x22| |CloneTemplate22x22|
          |FromImage22x22| |HuygensTemplate22x27|
          |ShareTemplate22x22| |FavouriteTemplate22x22|
          |DeleteTemplate22x22| show tooltips describing their actions w.r.t
          templates. Namely, **create**, **edit**, **clone**,
          **import from an image**, **import from a Huygens template**,
          **share**, **mark as favourite** and **delete**.


.. _decon_job_step3:

The Restoration Parameters (3/5)
================================

In step 3 - |RestorationParameters22x22| :ref:`Restoration Parameter<restoration_template>` -
the restoration settings can be specified and saved.
As in the :ref:`previous secion<decon_job_step2>` the restoration parameters are grouped in templates.
A template can be reused in future deconvolution jobs.
This will be useful when other images need to be restored with the same settings.
Moreover, the templates can be shared among HRM users, fostering collaboration and re-usage of good restoration settings.

The following selections are possible at this stage:

* **Admin restoration templates**: parameter templates created by the HRM
  administrator to be used as references. They can be copied and edited by
  the HRM users. In order to use them, they first need to be copied
  to **Your restoration templates** by using |DownArrow22x22|.

* **Your restoration templates**: the restoration templates that the user can
  use directly. All templates in this area may be selected, edited,
  removed, etc.

.. note:: |CreateTemplate22x22| |EditTemplate22x22| |CloneTemplate22x22|
          |HuygensTemplate22x27| |ShareTemplate22x22| |FavouriteTemplate22x22|
          |DeleteTemplate22x22| show tooltips describing their actions w.r.t
          templates. Namely, **create**, **edit**, **clone**,
          **import from a Huygens template**, **share**,
          **mark as favourite** and **delete**.


.. _decon_job_step4:

Analysis parameters (4/5)
=========================

In step 4 - |AnalysisParameters22x22| :ref:`Analysis Parameters<analysis_template>` - the analysis
settings for your images can be specified and saved. As always, the analysis
parameters are grouped in templates. A parameter template can be reused in
future deconvolution and analysis jobs. This will be useful when the same type
of analysis has to be performed on other images. Moreover, the parameter
templates can be shared among HRM users, fostering collaboration and re-usage
of good analysis settings.

The following selections are possible at this stage:

* **Admin analysis templates**: parameter templates created by the HRM
  administrator to be used as references. They can be copied and edited by the
  HRM users. In order to use them, they first need to be copied to
  **Your analysis templates** by using |DownArrow22x22|.

* **Your analysis templates**: the analysis templates that the user can use
  directly. All templates in this area may be selected, edited, removed, etc.

.. note:: |CreateTemplate22x22| |EditTemplate22x22|
          |CloneTemplate22x22| |ShareTemplate22x22| |FavouriteTemplate22x22|
          |DeleteTemplate22x22| show tooltips stating their action w.r.t
          templates. Namely, **create**, **edit**, **clone**, **share**,
          **mark as favourite** and **delete**.


Launch the job (5/5)
====================

In this last step several summaries display all the chosen parameters.

Also, the output format for the result images can be selected at the top
of the page:

|OutputFormatScreenshot|

* **ICS**, **ICS2** and **HDF5**: support multi-channel images, 32 bit dynamic
  range (preserve all image details) and all the microscopic metadata
  parameters. Furthermore, they support high compression levels. Since
  deconvolved images often contain background regions with near 0 intensities
  the compression algorithms usualy manage to greatly reduce the size of the
  images. For all these reasons these are the formats **recommended** for
  further work with Huygens.

* **TIFF**: this format can be used for analysis such as counting or
  segmentation. For quantification one needs to scale the TIFF image back
  to its original dynamic range. The corresponding scaling factors are
  reported by HRM and can be found in :ref:`parameter_summaries`.

* **IMS**, **OME-XML**, **R3D**: formats offered for compatibility with
  other programs.

Next, review all the selected parameters before submitting the job to the
server. It's possible to go back to the image, restoration, and analysis
template editors by clicking on the corresponding links.

Click on |ImageParametersLink| to change the image parameters.

|SummaryParamsScreenshot|

Click on |RestorationParametersLink| to change the restoration parameters.

|SummaryParamsScreenshot2|

Click on |AnalysisParametersLink| to change the analysis parameters.

|SummaryParamsScreenshot3|

To change the image selection click on |SelectedImagesLink|.

|SelectedImagesScreenshot|

Finally **submit** the job by pressing |SubmitJob30x22|.
