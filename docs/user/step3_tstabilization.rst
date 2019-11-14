.. include:: global_directives.inc

.. _t_stabilization:

Stabilization of time series
============================

This option will only be shown when restoring time series. In order to let
HRM know that an image batch contains time series please set the time interval
correctly, as explained in :ref:`voxel_size`.

The restoration template editor contains a section for post-deconvolution
operations. Options for these operations
(chromatic aberration correction and stabilization of time series) only show
up when applicable, i.e, multichannel images and time series. 

Therefore, the following option will only be displayed when restoring a time
series:

|TStabilizationScreenshot|

Set a stabilization method:

|TStabilizationScreenshot2|

* **Center of mass**: works best if the image contains a single large 
  object. No objects should cross the image borders.

* **Correlation**: for general x-y-z translations and axial rotations.
  Adjacent time frames will be compared. The software will try to find the
  best alignment by maximizing structural overlap.

* **Model based**: if the geometry of the imaged object did not change much
  during the acquisition.

Choose whether to detect and correct rotations:

|TStabilizationScreenshot3|

Lastly, specify the cropping mode for the resulting, stabilized time series:

|TStabilizationScreenshot3|

* **Original**: to crop the result to the size of the raw data.

* **Full**: to preserve the size of the stabilized data.

* **Tight**: to crop away large background regions.


.. note:: Depending on the cropping mode the dimensions of the result and
   the raw data will differ. This will become noticeable when comparing the 
   data later. See :ref:`detailed_view_results`.
