**********************************
Administrator’s guide
**********************************

Installation

Administrator’s options

How HRM communicates with Huygens Core

Requirements and technical features

Tips & Tricks



Administrator’s guide
=====================

Much information about the administration and maintenance is available
online on the HRM project server\ `16 <#50532361_pgfId-923770>`__.
Throughout this chapter some understanding of PHP is assumed.

|image75|

Installation

To install an HRM web-server several steps are required. There is a full
and extended installation guide available on the project’s
website\ `17 <#50532361_pgfId-919793>`__. Keep in mind that there are a
number of pre-requisites, also described on the website. Below the main
requisites are listed.

-  *Operating system:* Any recent linux distribution and Mac OS X 10.5
   (Leopard) and 10.6 (Snow Leopard) and 10.7 (Lion, though testing has
   so far been limited).
-  *Huygens Core:* HRM is just an interface and needs Huygens Core to do
   the calculations. Note that Huygens Core needs a license.
-  *Apache2 web server.*
-  PHP version 5.2+: Both the queue manager and the web interface are
   written in PHP and need PHP to operate.
-  *MySQL or PostgreSQL:* A relational database management system is
   required.

|image76|

Administrator’s options

There are a number of extra options available to the administrator, most
are self explanatory and will not be mentioned here. Some require
highlighting.

Create global templates
'''''''''''''''''''''''

The administrator can set global templates, which are accessible for all
users to use. This is useful to create a low threshold for beginning
users to start deconvolving their raw data. Additionally the
administrator may create a template for each setup present in the
facility. The templates hold the same properties as the users template.
Raw Images can be uploaded, so that the SNR estimator can be used when
creating a restoration template. The administrator can manage *Image
templates* (`See The Image Parameters
(2/5) <HRMUserManual.htm#50532397_23332>`__), *Restoration templates*
(`See The Restoration Parameters
(3/5) <HRMUserManual.htm#50532397_72620>`__) and *Analysis templates*
(`See Analysis parameters (4/5) <HRMUserManual.htm#50532397_74065>`__).

|image77|

Version upgrade
'''''''''''''''

To upgrade to a new version of HRM, download the latest version from
SourceForge\ `18 <#50532361_pgfId-920135>`__. Next, replace the old
version of HRM on your Apache web server with the new version you just
downloaded. For Linux use:

*cp -r /path/to/newHRM /path/to/oldHRM*

That’s it! The configuration file is created during installation and not
included in new versions, so the configuration file from the old version
will be conserved. When upgrading from old versions of HRM, please refer
to the project website\ `19 <#50532361_pgfId-920250>`__ for extra
information.

Database update
'''''''''''''''

The database backend of HRM contains all previously uploaded images and
created parameter sets and templates. Therefore it cannot simply be
deleted and replaced by a newer version.

HRM contains an option to easily update the database to the latest
version. Go to *Database update* from the main menu, on the right is an
update button which will automatically update the database to the latest
version. In order to get your system completely up to date, it is
advised to upgrade the version first and then update the database.

System configuration
''''''''''''''''''''

HRM can be configured during the installation, afterwards these settings
are saved in a configuration file. If some settings need to be adjusted,
for example the maximum upload limit, both the PHP configuration and the
HRM configuration file must be edited. PHP states its limits, from which
HRM may differ if allowed by the PHP settings.

For example, the PHP configuration file states a max upload file size of
256MB, this is applicable to all programs using PHP, the HRM
configuration states that the max upload limit is 200MB, since 200MB is
lower than 256MB, the HRM configuration does not conflict with the PHP
configuration and 200MB is the maximum allowed file size.

The path to the PHP configuration file:

*/path/to/php/php.ini*

The path to the HRM configuration file:

*/path/to/hrm/config/hrm\_client\_config.inc*

|image78|

How HRM communicates with Huygens Core

For each deconvolution task in the job queue the HRM queue manager
automatically generates a Huygens Batch template for Huygens Core that

-  loads the raw image from a source directory,
-  applies the microscopic parameters to it as defined by the user or
   reads the microscopic parameters from the image metadata,
-  optionally loads another image containing the microscope Point Spread
   Function,
-  deconvolves the image using the restoration parameters chosen by the
   user,
-  stores the resulting restored image in a destination directory,
-  generates a number of visualizations of the raw and deconvolved
   images so that the user can see the effect of the restoration,
-  and finally writes a tag in the destination directory to inform the
   HRM queue manager that the job is finished.

 

When the job is finished the queue manager optionally sends the user an
e-mail announcing the end of the job and its status. The administrator
may configure this.

Multiple jobs can be processed in parallel depending on how HRM is
configured, the multiprocessing capabilities of the server and the
number of available computation servers.

|image79|

Requirements and technical features

HRM consists of two main components: a web based interface and a queue
manager. The web interface allows:

-  the management of users by the system administrator;
-  the management of parameter sets that all users can copy or use
   directly;
-  the creation of deconvolution jobs, including image selection,
   setting microscopic parameters, and setting restoration parameters;
-  inspecting the job queue status, and allowing the users to delete
   their own jobs from it.
-  previewing and colocalization-analyzing deconvolved images, including
   a slicer, MIP and SFP.

HRM is equipped with a simple http file uploader/downloader to send raw
images from the user’s local machine to the HRM server, as well as to
retrieve the deconvolution results from the server. The server
administrator can set up a limit for these transactions.

The jobs created via the web interface are dispatched by the HRM queue
manager, which runs in the background, to any of the dedicated servers
running Huygens Core. When the job is finished, an e-mail may inform the
user that the restored datasets are available.

HRM requires:

-  A web server with PHP and e-mail capabilities.
-  A database backend to store deconvolution parameters, job
   descriptions and, optionally, user accounts.
-  A file server to temporarily store input and restored datasets.
-  One or more processing servers running Huygens Core.

The setup is highly configurable, sincethe file server, the processing
servers and the queue manager can either be all hosted by the same
machine or be distributed across two, three or more computers.

 

--------------

1. http://sourceforge.net/projects/hrm

2. http://www.svi.nl/HuygensRemoteManager

3. http://www.huygens-rm.org

4. http://www.svi.nl/HrmInstallation

5. http://hrm.svi.nl

6. http://www.svi.nl/Colocalization

7. http://hrm.svi.nl

8. http://www.snapfiles.com/get/denrenamer.html

9. http://www.svi.nl/NyquistRate

10. http://www.svi.nl/MismatchDistortsPsf

11. http://www.svi.nl/MaximumIntensityProjection

12. http://www.svi.nl/SFP

13. http://www.svi.nl/ColocalizationBasics

14. http://www.svi.nl/ColocalizationTheory

15. http://www.svi.nl/2DHistogram

16. http://huygens-rm.org/home/

17. http://huygens-rm.org/home/?q=node/6

18. http://sourceforge.net/projects/hrm/

19. http://huygens-rm.org/home/?q=node/5

