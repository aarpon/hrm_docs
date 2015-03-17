.. include:: global_directives.inc

.. _step5:


Launch the job (5/5)
====================

In this last step several summaries display all the parameters with which the
job will be submitted.


The output format of the restored images can be adapted with the top drop-down widget.

|OutputFormatScreenshot|

* **ICS**, **ICS2** and **HDF5**: support multi-channel images, 32 bit dynamic
  range (preserve all image details) and all the microscopic metadata
  parameters. Furthermore, their compression level is very good, since
  deconvolved images often contain background regions with near 0 intensities
  the compression algorithms typically do a great job. These are the
  **recommended** formats for further work with Huygens.

* **TIFF**: this format can be used for analysis such as counting or
  segmentation, but **not** for quantification.

* **IMS**, **OME-XML**, **R3D**: formats offered for compatibility with
  other programs.

Next, review the parameters. First the image paramters. Notice that it's
possible to go back to the corresponding template editor by clicking on
|ImageParametersLink| :

|SummaryParamsScreenshot|

Then the restoration parameters. Click on |RestorationParametersLink| to
change the parameter selection.

|SummaryParamsScreenshot2|

And lastly the analysis parameters. Click on |AnalysisParametersLink| for
further changes.

|SummaryParamsScreenshot3|


To change the image selection click on |SelectedImagesLink|.

|SelectedImagesScreenshot|

Finally **submit** the job by pressing |SubmitJob30x22| .

