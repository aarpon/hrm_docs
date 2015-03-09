.. include:: global_directives.inc

**********************************
Administrator’s guide
**********************************

To download the latest version of HRM please click `here <http://sourceforge.net/projects/hrm/files/latest/download>`_.


Installation
============

To install HRM the following pre-requisites (at least) must be fulfilled:

* **Operating system**: Any recent Linux distribution. Ubuntu and Fedora are
  the recommended distro's for HRM.
* **Huygens Core**: HRM is just an interface and needs Huygens Core to
  perform deconvolution on images. Note that Huygens Core needs a license.
* **Apache2 web server**.
* **PHP version** |ge| **5.3**:
  Both the HRM queue manager and the web interface are
  written in PHP and need PHP to operate.
* **MySQL or PostgreSQL**:
  A relational database management system is required.

  To follow the list of guided installation steps please see `the installation
  page at the HRM project’s site <http://huygens-remote-manager.readthedocs.org/en/latest>`_. 



Administrator’s options
=======================

Log in to HRM with the credentials of the administrator. Instead of the
regular user home panel HRM will display the administrator home panel, like
this:

|AdminHomePanelScreenshot|

There are a number of extra options that are available to the administrator
only:

* **Create global templates**: The administrator can create global templates
  accessible to all users. This is meaningful for lowering the threshold
  for those beginning users who need assistance to start deconvolving their
  raw data. Global templates can be created at any of the states where
  templates are required: :ref:`step2`, :ref:`step3` and :ref:`step4`.
  

Version upgrade
===============

Before upgrading HRM please proceed to backup the HRM database, images and
source files.

To upgrade to a new version, download the latest version `from here
<http://sourceforge.net/projects/hrm/files/latest/download>`_. Next, replace
the source files of the old version with those of the new version.
For Linux use something like:

.. code-block:: sh
                
   cp -r /path/to/newHRM /path/to/oldHRM*

Because the configuration file is not in new versions, your existing
configuration will be conserved.

For intructions on **specific version upgrades** please refer to `this page
at the HRM project's site <http://huygens-remote-manager.readthedocs.org/en/latest/upgrade.html>`_


Database update
===============

HRM's database contains the existing users, statistics,
parameter templates, etc. Therefore it should not be deleted and replaced
by a newer version. Instead, the database should be upgraded to the new
version. To do so, click on `Database Update` |UpdateDB22x22| from the admin
home panel and follow the instructions to get the database upgrade.

In order for this update to work properly it is advised to upgrade the
HRM source code first and then the database.

System configuration
====================

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
======================================

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
===================================

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


Tips & Tricks
=============


 

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

