.. include:: global_directives.inc


Import metadata
===============

Notice that the previous parameters showed a "`footnote`" like the following:

|MetadataScreenshot|

This is to make a distinction between the parameters that HRM requires from the
user and those which can be imported from the raw images.

In other words, some parameters can be imported from the image metadata at run
time, while deconvolving the image, to save you time. In such cases, one
doesn't need to enter a value for the parameter in the template.

The way HRM lets you know when a parameter can be skipped and when it can't is
by providing "`footnotes`" next to the parameter.


.. note:: Because some microscopy file formats allow for **restricted** or
          **no metadata** HRM signals that a parameter may be missing from
          the metadata of a batch of images, like this: |MetadataScreenshot3| 
          
.. note:: Fortunately, other microscopy file formats do allow for all sorts of
          metadata. When working with such formats many parameters can be
          skipped. |MetadataScreenshot2|

At the end of the deconvolution job, HRM informs on the values of all used
parameters as well as their origin.
