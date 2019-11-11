.. include:: global_directives.inc

             
Using a measured PSF
====================

This option will only appear if 'measured PSF' was selected as PSF Type in a previous step.

Distilled PSFs need to be created beforehand using Huygens Professional and placed
in the src folder on the HRM drive.

.. note:: It is important to use only one image per channel, 
			multichannel PSFs are not supported.
          

When presented with the **Distilled PSF file selection**-window,

|DistilledPsfFileSelection1|
			
			
browse for the distilled PSF appropriate for the channel(s) of the image.

|DistilledPsfFileSelectionBrowse|
			
			

Choose the PSF fileS and click close. Repeat for all channels.

|DistilledPsfFileSelection2|
			
			

Afterwards, press save and return to the image parameter selection page.

.. note:: Files that can't work as PSFs for the selected image(s) are
          crossed off and displayed in red and.
          
		  

