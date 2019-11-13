.. include:: global_directives.inc

             
Using a measured PSF
====================

This option will only appear if 'measured PSF' was selected as PSF Type in a
previous step.

Distilled PSFs need to be created beforehand using Huygens Professional and
uploaded to the **Raw images** folder.

.. note:: One PSF image per channel. Mltichannel PSFs are not supported.
          

When presented with the **Distilled PSF file selection** window,

|DistilledPsfFileSelection1|


browse for the distilled PSF appropriate for the channel(s) of the image.

|DistilledPsfFileSelectionBrowse|



Select the PSF file and click close. Repeat for all channels.

|DistilledPsfFileSelection2|


Afterwards, press save and return to the image parameter selection page.

.. note:: Files that can't work as PSFs for the selected image(s) are
          crossed off and displayed in red.
           

