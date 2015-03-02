Background mode
===============

The background is a more or less constant value, which is added to the
image. Three options are available for the background correction. They
return slightly different values so this choice can affect the
deconvolution result:

-  *Automatic background estimation* : This estimation usually works
   fine. A region with a low mean value is found and the background
   computed there.
-  *In/near object* : Huygens estimates the background around intensity
   peaks. This option can be interesting, for example, when having
   bright little objects in a cell with a strong cytoplasmic background.
-  *Remove constant absolute value* : To make sure that the same
   background level is removed from all the images in the batch, insert
   manually a measured mean background for each channel. This option is
   typically useful for those interested in doing fluorescence
   quantification or stitching.
