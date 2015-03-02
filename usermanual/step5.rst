Launch the job (5/5)
====================

In this last step several tables are shown listing the images and
settings for the batch deconvolution.

The format of the output images can be selected here. As a guide one can
stick to the following rules. For 3D analysis the “ICS format” is
appropriate, or even the most recent “ICS2”, which is a multichannel,
32-bit format that stores all the deconvolution information while it
preserves all important details. For 2D imaging, when analysis is
required, the TIFF-8bit can be used for output. This format is fine for
analysis such as counting or for segmentation, but not for
quantification. For 2D quantification 16-bit or 32-bit formats are
recommended. For 3D visualization with Huygens ICS, ICS2 or HDF5 are
most appropriate.

|image58|

To change the images or the settings of the Batch Deconvolution click on
the corresponding links: *Image Parameters* , *Processing Parameters* ,
*Analysis Parameters* *and* *Selected Images* .

To launch the deconvolution click on the *big green button* at the
bottom of the page (See `See Launch. Select the output file format and
launch. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_52511>`__). HRM
will create one job per image and put it in the job queue.

|image59|

After launching the jobs HRM shows the main panel. Click on the *Queue
Status* icon to examine the jobs status or to delete them if they are no
longer needed.

|image60|
