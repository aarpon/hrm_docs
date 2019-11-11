.. include:: global_directives.inc


STED parameters
===============

If the selected microscope type is **STED** or **STED 3D** then a few
STED parameters need to be specified to describe the STED acquisition.
When working with other microscope types HRM will skip these parameters.

First, select the STED depletion mode: **Pulsed**, **Continous wave gated
detection**, **Continous wave non gated detection** or **Off/Confocal**.

|STEDModeScreenshot|

.. note:: **STED and confocal microscopy are often combined**. That's
          why even if the selected microscope type is STED it's still possible
          to set specific channels as **confocal** at this point.

Set the STED saturation factor of each channel. Typical values are in
the range of 10 to 50. The higher this factor, the more suppression of
fluorescence away from the optical axis, the more resolution.

|STEDSaturationScreenshot|
          
Next, set the STED depletion wavelength of each channel. Notice that
Channel 1 is grayed out in these figures because it was set as confocal.

|STEDWavelengthScreenshot|

The STED immunity fraction tells Huygens the percentage of fluorescent
molecules that are not susceptible to the STED laser. Typical values are in the
range 0% to 10%.

|STEDImmunityScreenshot|

Finally, depending on whether the microscope type is STED 3D or not, set the
percentage of STED 3D per channel. This tells Huygens how much power was used
in the Z depletion beam. The remaining power is used for the vortex path.

|STED3DScreenshot|
