.. include:: global_directives.inc


SPIM parameters
===============

If the selected microscope type is **SPIM** then a few
SPIM parameters need to be specified to describe the SPIM acquisition.
When working with other microscope types HRM will skip these parameters.

First, select the SPIM excitation mode of each channel:
**Gaussian light sheet**, **Gaussian MultiView light sheet**,
**High fill factor (cylinder)**, or **High fill factor (scanning beam)**.

|SPIMExcModeScreenshot|


Set the width of the Gaussian light sheet for the channels acquired with one
of the Gaussian modes. The field will be grayed out for the other channels.

The width is defined as the distance between the two (symmetric) points  of
the Gaussian profile where the intensity values drop to 2/e^2 of the peak value.


|SPIMGaussWidthScreenshot|


Set the SPIM Focus Offset of the light sheet. This is the distance along the
optical axis of the detection lens between the focus of the illumination
lens and the focus of the detection lens.

|SPIMFocusScreenshot|


Similarly, set the SPIM Center Offset of the light sheet. This is the distance
along the optical axis of the illumination lens between the focus of the
illumination lens and the focus of the detection lens.


|SPIMCenterScreenshot|


Set the SPIM NA for the channels aquired with the one of the High Fill Factor
modes. This is the Numerical Aperture of the illumination lens.


|SPIMNAScreenshot|


Then, the fill factor of the illumination lens, for the channels acquired with
one of the High Fill Factor modes. This is the ratio between the beam width
and the diameter of the objective pupil in the illumination lens.


|SPIMFillScreenshot|


Lastly, the SPIM Illumination Direction. This can be left, right, bottom, top
for any of the non-MuVi (Multi-View) excitation modes; and right+left or
top+bottom for the Gaussian MuVi excitation mode.


|SPIMDirectionScreenshot|
