.. include:: global_directives.inc

.. _step5:


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

