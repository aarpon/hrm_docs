.. include:: global_directives.inc

.. _detailed_view_results:

************************
Results: detailed view 
************************

When the job finishes, the files are placed in the |Results22x22|  **Results**
folder, accessible via the home panel.

Click on an image result for further inspection as explained in
:ref:`results` .
     
The detailed view shows the following information:

* `MIP <http://www.svi.nl/MIP>`_ of **original** vs **deconvolved**,
* `SFP <http://www.svi.nl/SFP>`_    of **original** vs **deconvolved**,
* Z Slicer of **original** vs **deconvolved**,
* T Slicer of **original** vs **deconvolved**,
* Stack movie of **deconvolved**,
* T movie of **deconvolved**,
* T SFP movie of **deconvolved**,
* Colocalization results,
* Parameter summaries,
* Huygens log.

.. note:: The number of tools shown in the detailed view depends on the type
          of restoration, the image geometry and the HRM configuration.

  
Comparing MIPs
==============

A comparison of the Maximum Intensity Projections of the raw image and the
restored image shows the effect of deconvolution.

|MIPResultScreenshot|

Comparing SFPs
==============

A comparison of the Simulated Fluorescense Process in both the raw image and the
restored image also shows the effect of deconvolution and difference in noise.

|SFPResultScreenshot|

Comparing Z Slices
==================

The slicer allows for a comparision of the raw image and the restored image
slice by slice along the Z direction at any depth.

|ZSlicerResultScreenshot|

Comparing T frames
==================

The time slicer allows for a comparision of the raw image and the restored image
frame by frame.

|TSlicerResultScreenshot|

Z, T and T-SFP movies
=====================

Click on the corresponding links to download any of the movies to your local
computer.

|MoviesLinks|

.. note:: Notice how useful these automatically made movies are for
          prepraring presentations. 

Colocalization
==============

The selected colocalization coefficients of each two channels are listed
in a table with an entry per frame.

|ColocTableScreenshot|

Also, `2D histograms <http://www.svi.nl/2DHistogram>`_ show the correlations
between any two channels.

|2DHistogramScreenshot|

Lastly, the colocalization maps show the regions where colocalization between
any two channels is strongest.

|ColocMapsScreenshot2|


Parameter summaries
===================

HRM also gives feedback on all the parameter values used during deconvolution.
This is particularly useful when the parameters are read from the image
metadata. 

|ParameterSummaryScreenshot|

Notice that green entries indicate parameters loaded from the image metadata,
whereas violet entries indicate parameters defined by the user.

Huygens log
===========

The exact steps followed by Huygens to process the data can be found on the
Huygens log, under the link |HuygensLogLink| .


.. note:: Notice that all these results along with the deconvolved dataset
          can be **donwloaded** by clicking |DownloadResults22x22| .
