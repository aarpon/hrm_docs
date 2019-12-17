.. include:: global_directives.inc

.. _step1:
   
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
