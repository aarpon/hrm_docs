Import metadata
===============

Most microscopy file formats allow for saving metadata. If the
acquisition system works with such file formats it can save parameters
such as the sampling sizes, pinhole sizes, numerical aperture, etc, in
the raw data. In HRM the user can choose whether this information (image
metadata) should be used in the deconvolution job. Some file formats,
though, lack the structure to save all the relevant information of a
parameter, e.g. physical units. For this reason, HRM informs, per file
type, how reliably the metadata can be used (see `See Metadata warnings.
When trusted metadata is present, HRM will inform on this, leave blank
to adopt metadata
values. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_35175>`__). Leave
fields blank to accept the metadata. HRM assists the user in this
regard, showing messages on which parameters may be skipped and which
must be provided. Notice that entering the image parameters for a
deconvolution job in HRM can be skipped almost entirely if the images
contain good, complete, reliable metadata, while the deconvolution
results will be optimal.

|image34|

|image35|

At the end of the deconvolution job, the user may get a notification
email and a link to the restored image, a summary table can be viewed
listing which parameters were taken from the metadata, as well as their
values (see `See Parameters used during deconvolution. Parameters
retrieved from the image metadata are also
shown. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_70726>`__).

|image36|

When entering the image parameters, the following properties are
relevant (See `See Raw images section. Files can be uploaded and deleted
here.`).
