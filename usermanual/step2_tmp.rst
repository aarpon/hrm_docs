


-  *Objective type* : Dry or immersion objective (oil, water, glycerol,
   air).
-  *Sample medium* : The refractive index of the medium in which the
   sample was embedded (glycerol, polyvinyl alcohol, vectashield or
   other media).
-  *Voxel size* : The voxel size is a very important parameter for the
   deconvolution of microscopic images. According to the Nyquist
   criterion\ `9 <#50532361_pgfId-982893>`__ its value should not be
   larger than half the optical resolution of the imaging system. In
   order to set the voxel size appropriately three different cases can
   be distinguished depending on the microscope type.
-  *Voxel size, widefield and spinning disk microscopy* : On widefield
   images, the *xy* pixel size depends on the physical size of the CCD
   camera element, the objective magnification, the binning, and the
   possible magnification factors introduced by the microscope tube and
   the c-mount. In the frequent case in which the tube factor and the
   c-mount factor are equal to 1, the *xy* pixel size is given by:

|image39|

If a pixel binning is used, it is necessary to take this into account to
calculate the pixel size. HRM gives access to a calculator to compute
the *xy* pixel size (see “Calculate from CCD pixel size” at the image
parameters page). HRM also shows the ideal voxel size for the given
optical parameters (numerical aperture, refractive indexes, etc) so that
it can be used as a reference. Make sure to set a voxel size consistent
with the optical resolution of the microscope as undersampled images
will often show artifacts after deconvolution. Notice that the z-step
value can often be found in the metadata of the image.

-  *Voxel size, confocal and 2-photon microscopy* : When using batch
   processing, the parameters for all images need to be the same. In
   case of confocal and widefield microscopy, the voxel size is affected
   by the zooming factor and the frame size for a given objective.
-  *Backprojected pinhole radius (for confocal and 2-photon microscopy,
   shown in `See (a) First optical parameters page. Only the microscope
   type must be provided. (b) Second optical parameters page. Some
   settings are only applicable for some
   microscopes. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_62198>`__)*
   : In confocal images the “backprojected pinhole radius” is the radius
   of the pinhole as it would be seen on the focal plane. This number
   can be calculated in HRM by clicking on the “Backprojected pinhole
   calculator” link. The calculator will ask for the objective
   magnification and the actual pinhole radius for the computation of
   the backprojected radius.
-  *Backprojected pinhole spacing and radius (for* *Spinning disk
   microscopy)* :

HRM also counts on a calculator to compute the backprojected value of
the pinhole spacing for spinning disk microscopy (See `See Select files
to measure PSF from. Active when a measured PSF is
chosen <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_29035>`__). This
calculator lists a number of microscope models to assist the user in the
calculation. If, for example, a Yokogawa disk is selected from the list,
the pinhole radius is set to 250 nm and the pinhole spacing is set to
2.53 μm. From these values, combined with the magnification, HRM
computes the backprojected counterparts (as they would be seen on the
focal plane).

|image40|

As the Point Spread Function (PSF) is the basic “brick” of which the
images are “made”, one should record details at least on the scale of
the PSF to gather all the available information. Failing at that may
spoil any attempt to do deconvolution, because deconvolution works on
the PSF scale. If a voxel is much larger than the PSF, the deconvolution
simply cannot be done, then there are many PSF’s recorded in one voxel
and it becomes impossible to distinguish between those. In HRM, one can
choose to have Huygens Core calculate a theoretical PSF compatible with
the raw image or one can upload the measured (distilled) PSF that most
resembles the real PSF of the imaging system. In practice the
theoretical PSF computed from the image parameters can significantly
differ from the experimental (distilled) PSF, because of unavoidable
little misalignments and imperfections in the microscope system. Usually
a measured PSF is larger and more asymmetric than a theoretical one. The
use of a measured PSF can thus improve the deconvolution results.

-  *Distilled PSF file selection* : A measured PSF can be derived from
   images of fluorescent beads, for example using the SVI Huygens PSF
   Distiller. However a good PSF is relatively complicated to measure,
   as one needs to acquire multiple images for each wavelength.
   Additionally the measurement must be done with the exact same
   conditions as the images for which the PSF is intended (See `See
   spherical aberration correction. Schematic guideline to spherical
   aberration correction
   methods. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_82680>`__). HRM
   will ask to select one PSF file per channel if a measured PSF option
   is chosen. When selecting a file, those files that don’t suit the
   current image parameters are highlighted in red to stress that they
   are not good PSF candidates.

|image41|

-  *Theoretical PSF, spherical aberration correction* : if necessary HRM
   will ask whether to correct the theoretical PSF for spherical
   aberration (See `See Spherical aberration correction. Specify which
   correction to
   use. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_57129>`__). In
   general, better deconvolution results are achieved if the spherical
   aberration correction is applied. A few more parameters are necessary
   for the spherical aberration correction. `See spherical aberration
   correction. Schematic guideline to spherical aberration correction
   methods. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_82680>`__ shows
   a schematic guideline to the different methods of correction. Note
   that these are only guidelines and the applicability of each method
   differs per case.
-  *Specify sample orientation* : Specify the position of the coverslip
   with respect to the dataset (*Plane 0 is CLOSEST / FARTHEST from the
   coverslip* ).

-  *Correction mode* : Due to the spherical aberration the PSF size and
   shape changes with the sample depth. To correct for this effect
   Huygens Core will generate a “dynamic” PSF adapted to the different
   positions\ `10 <#50532361_pgfId-994959>`__. Use the Spherical
   Aberration correction only if there is a significant mismatch between
   the refractive indexes of the objective and of the sample medium, as
   the processing is significantly more time-consuming.

|image42|

#. *Deconvolution with PSF generated at user-defined depth (advanced)* :
   A unique PSF will be used, but calculated at a sample depth defined
   by the user. The main idea is to use a “mean” PSF to partially
   correct for spherical aberration. Useful when a user is interested in
   an object at a specific depth.
#. *Perform automatic correction* : In this case the stack will be
   divided into a certain number of bricks. Each brick will be
   deconvolved with a PSF adapted to the depth, considering the mismatch
   of refractive indexes between the sample medium and the objective
   medium.
#. *Depth-dependent correction on few bricks (advanced)* : The number of
   bricks into which the stack will be divided for the deconvolution is
   limited. The deconvolution will be faster than in the case “Perform
   automatic correction”.
#. *Depth-dependant correction performed slice by slice (advanced):* A
   new PSF is calculated for each slice.

At this point, the parameter set is ready and can be saved. The list of
all the user’s parameter sets will be shown.

Select one parameter set for the deconvolution job and click on the big
*right arrow* to continue (see `See Image parameters, main
page. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_15842>`__).

|image43|

|image44|
