******************
The Results Folder
******************

After deconvolution has finished, the files are placed in the *results*
*folder* , accessible via the main menu. From here, results can be
viewed and edited or downloaded directly. There is a preview available
on the right panel. Additionally, HRM comes with a analysis tools to
compare the deconvolved result with the original data, accessible
via\ ** *Go to detailed results* button on the right panel.

The tools available, depending on the features of the image, are an
MIP\ `11 <#50532361_pgfId-956703>`__ (Maximum Intensity Projection), an
SFP\ `12 <#50532361_pgfId-956727>`__\ (Simulated Fluorescence Process),
a Slicer and a Stack movie which can all be downloaded by the user. With
these tools it can be examined online whether the deconvolution result
is satisfactory.


Let us take a closer look at the image comparison tools. Upon entering
the user is given an *MIP* view, which shows only the voxels which have
an intensity higher than a certain value. Via the left menu, several
other tools are available. `See MIP comparison tool. A Maximum Intensity
Profile view, compare the original (left) to the deconvolved image
(right). Image courtesy of Drs. Jeff
Tucker. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_54123>`__ shows a
typical MIP result, comparing the original image with the deconvolved
data set.

The original raw data and deconvolved image can also be compared as
*SFP* rendered images (see `See SFP comparison tool. An SFP, simulated
Fluorescence Process, a tool to compare the original (left) with the
restored image (right). Image courtesy of Jeff
Tucker. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_55164>`__).
Basically, an SFP renders the shadow profile of your object on a
homogeneous plate. If there is an area with a high absorption
coefficient in the image, this area may absorb all the excitation light
and cast a shadow over other parts of the object, making them difficult
to image. .


The *Slicer* allows the user to compare the original image and the
deconvolved data set slice by slice along the z coordinate at any depth
(See `See Slicer tool. A slicer tool for 3D images, which allows the
user to compare individual z-slices. Image courtesy of Anko de
Graaff. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_13076>`__).


The colocalization tool allows the user to do colocalization analysis of
the image. There are several options and coefficients available, which
have been selected during the analysis parameters stage of the launching
procedure. It is important to understand what these coefficients do in
order to interpret them. Full information and details about different
colocalization coefficients can be found on the
website\ `13 <#50532361_pgfId-993687>`__
`14 <#50532361_pgfId-993706>`__.

Upon opening the colocalization analyzer, the coefficients page is
displayed. Here the different coefficients for each two channels are
shown, as well as a 2D colocalization
histogram\ `15 <#50532361_pgfId-993732>`__, as shown in `See
Colocalization coefficients and histogram. No clear colocalization is
found. Note that other channel sets have been omitted. Image from Jeff
Tucker. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_38805>`__.


The colocalization map page can be accessed using *Coloc Maps* in the
top menu. A colocalization map will be shown for each set of channels
for the parameter the user selected. On the left the two deconvolved
source channels are shown, while on the right the colocalization results
can be viewed.


Note that there are two Manders coefficients and each channel (Red and
Green) in the right image shows a Manders coefficient (M1 and M2), as
seen in `See Colocalization map. On the left the two deconvolved
channels are shown, on the right the colocalization map for the two
Manders coefficients. Image from Jeff Tucker. Note that other channel
sets have been
omitted. <HRM/HRM%20Deconvolution%20Jobs.htm#50532397_23965>`__. Other
coefficients are singular and show only one channel.

There are several download options available to the user. Not all
options are available for all images, depending on whether the image has
a z- or time dimension.

-  *Z-stack movie:* Use the *stack movie* button to download a .avi
   file, which plays the z-slices in consecutive order.
-  *MIP time movie:* Use the *series movie* to download a .avi file,
   which plays the MIP projection of your file in time.
-  *SFP time movie:* Use the *series SFP movie* to download a .avi file,
   which plays the SFP projection of your image in time.
-  *download deconvolved data:* Use the *download icon* to download the
   deconvolved data, this includes all accessory files.

