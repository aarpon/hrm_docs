.. include:: global_directives.inc

.. _omero_integration:

OMERO connector
==================================

HRM can import and export images from/to a local or remote  `OMERO
<http://www.openmicroscopy.org/site/products/omero>`_ server. 

.. note:: This feature is not active by default. Ask the HRM
          administrator for more information about the HRM/OMERO connector.

If the connection between HRM and OMERO is enabled the OMERO logo |OMERO22x22|
will be is displayed in the `Raw images` |RawImages22x22| and
`Results` |Results22x22| folders.

Click on |OMERO22x22| . The following window will ask you to enter your OMERO
login credentials.

|OmeroCredentialsScreenshot|

Upon logging in successfully a file tree will be displayed listing all the
images in the OMERO repository that you are allowed to visualize, like this:

|OmeroTreeScreenshot|

.. note:: The OMERO credentials and file tree will be used throughout the HRM
          session. When the session is closed HRM will remove the OMERO
          credentials from the cache.

The OMERO tree is requested automatically only the first time in every HRM
session. This saves waiting time in subsequent import/export operations with
OMERO. To force a tree rebuild click |Refresh22x22| .

The following actions are possible:

* **Import data from OMERO**: In the `Raw images` |RawImages22x22| folder
  select an image from the OMERO tree and click |UpArrow22x22|. The image
  will be imported to HRM with extension .ome.tiff. Select more images
  with Ctrl + click for importing multiple images in one go.

* **Export data to OMERO**: In the `Results` |Results22x22| folder select the
  HRM image to be exported. Select the target OMERO dataset. Click
  |DownArrow22x22| . The image will be attached to the OMERO project with an
  annotation describing all the parameters used for deconvolution. Select more
  images from the Results folder for exporting multiple images in one go.
