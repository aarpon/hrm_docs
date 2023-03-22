.. include:: global_directives.inc

*************************************
Edit hrm_config.inc (web-application)
*************************************

These configurations concern PHP, hence the web-application (front end) itself.

Copy the sample file
====================

Copy ``$HRM_SAMPLES/hrm_config.inc.sample`` to ``$HRM_CONFIG/hrm_config.inc``:

.. code-block:: sh

    sudo cp -v $HRM_SAMPLES/hrm_config.inc.sample $HRM_CONFIG/hrm_config.inc


Edit the configuration file
===========================

Here we will assume a one-machine installation:

.. code-block:: php

    <?php
    // This file is part of the Huygens Remote Manager
    // Copyright and license notice: see license.txt

    // This configuration file is used by the QUEUE MANAGER.

    //==============================================================================
    // Database settings
    //==============================================================================

    // The database type ('mysqli' or 'postgres'; mysql is deprecated).
    // Please notice that it is highly recommended to use the mysqli driver for
    // PHP 5.5 and above. In PHP >= 5.6, the mysql driver is deprecated and will
    // overflow your log files when used!
    $db_type = "mysqli";

    ?>

.. note::

    Although the database abstraction library (`ADOdb <http://adodb.sourceforge.net/>`_) we use in the HRM can interface with a large number of databases, we currently only support **MySQL** and **PostgreSQL**. Other DBs may work, but we haven't tested them.

.. note::

    Also, please use the **'mysqli'** driver instead of **'mysql'** as in previous versions of the HRM. From PHP 5.6, the 'mysql' driver is deprecated!

.. code-block:: php

    <?php
    ...
    // The name of the database host machine (this may be localhost if it is the 
    // machine on which the web server runs)
    $db_host = "localhost";
    
    // The name of the database used by HRM
    $db_name = "hrm";

    // The name of the user with which the database is accessed
    $db_user = "hrm";

    // The password of the account with which the database is accessed
    $db_password = "dbpasswd";

    //==============================================================================
    // Huygens settings
    //==============================================================================

    // Huygens server default user
    $huygens_user = "hrm";
    $huygens_group = "hrm";
    ?>

The ``$huygens_user`` is used in case the processing machine (the one where Huygens Core is installed) does not have direct access to the file server (i.e. the files to be deconvolved must be copied from the file server to the processing machine via ssh). For this to work, you will need to set up password-less ssh connection between file and processing server for the ``$huygens_user`` (see for example `here <http://www.debian-administration.org/articles/152>`_) and also set the variable ``$copy_images_to_huygens_server`` to ``true`` (see below).

.. code-block:: php

    <?php
    ...
    // Path to a local Huygens Core executable, to handle image information and
    // thumbnails. This installatation of hucore doesn't require a full license
    // unless this is also the computation server. For image information and
    // thumbnails mostly freeware functions will be used, but support for certain
    // propietary file formats requires a B flag in the license string. (See
    // http://support.svi.nl/wiki/FileFormats).
    //
    // In combination with Huygens 3.5.1 or higher, HRM can also provide an
    // estimate of the Signal-To-Noise ratio (SNR) of an image, interactively. At
    // least that same simple license is required for this to work.
    $local_huygens_core = "/usr/local/bin/hucore";
    ?>

The web interface uses hucore for some operations on the input and result files (for example to generate image previews or estimate the SNR interactively). An additional copy of hucore needs therefore to be installed on the web server. However, since all these functions used are accessible in reader mode, only a reader license is needed (free of charge).


.. code-block:: php

    <?php
    //==============================================================================
    // File server settings
    //==============================================================================

    // File server host name
    $image_host = "localhost";

    // File server default user
    $image_user = "hrm";
    $image_group = "hrm";

    // File server base folder
    $image_folder = "/data/hrm_data";

    // File server image source folder
    $image_source = "src";

    // File server image destination folder
    $image_destination = "dst";

    // File server base folder as seen from the Huygens server machines
    $huygens_server_image_folder = "/data/hrm_data";
    ?>
    
This is information needed for the web interface and the queue manager to login to the file server. If the file server is not on the same machine, its host name must be given.

.. code-block:: php

    <?php
    ...
    // Allow HTTP transfer of the restored (download) images
    $allowHttpTransfer = true;

    // Allow HTTP transfer of original (upload) images.
    // Limitations in upload size must be configured in the below parameters 
    // $max_upload_limit AND $max_post_limit. If these are set to 0, they are  
    // instead read from the PHP settings. If set to higher values, make sure
    // that the PHP settings allow for such transfer limits. These PHP settings
    // are normally located in php.ini, with the options upload_max filesize AND 
    // post_max size.
    // Unzipping large archives may also require high max_execution_time and
    // memory_limit variables.
    $allowHttpUpload = true;
    $max_upload_limit = 0; // Maximum file size for uploads in Mb
    $max_post_limit = 0;   // Maximum post size for uploads in Mb

    // Archiver for downloading the results via the web browser:
    // $compressBin is the archiver, including options.  %DEST% will be replaced
    // with the user's destination path; can be used as an option or part of the
    // command to change directories with 'cd'. Separate commands with "\n".
    // $packExcludePath controls whether the archiving command excludes the whole
    // file path per file when this is taken into account in the $compressBin
    // command itself by using %DEST% properly.

    $compressExt = ".zip";

    switch ($compressExt) {
        case ".tgz":
        case ".tar.gz":
            $compressBin = "cd %DEST% \n /bin/tar chzf ";
            $packExcludePath = true;
            $dlMimeType = "application/x-force-download";
            break;
        case ".tar":
            $compressBin = "cd %DEST% \n /bin/tar cfh ";
            $packExcludePath = true;
            $dlMimeType = "application/x-force-download";
            break;
        case ".zip":
            $compressBin = "cd %DEST% \n /usr/bin/zip ";
            $packExcludePath =true;
            $dlMimeType = "application/x-force-download";
            break;
        default:
            $compressExt = ".zip";
            $compressBin = "cd %DEST% \n/usr/bin/zip -D";
            $packExcludePath = true;
            $dlMimeType = "application/x-force-download";
    }

    // Tools to decompress uploaded archives. This is an array, each key linked to
    // an archive extension.  %DEST% will be replaced with the user's destination
    // path; can be used as an option or part of the command to change directories
    // with 'cd'.
    // More formats are possible, just add more commands to the array.

    $decompressBin['zip'] = "cd %DEST% \n /usr/bin/unzip -o ";
    $decompressBin['tgz'] = "cd %DEST% \n /usr/bin/tar xzf ";
    $decompressBin['tar'] = "cd %DEST% \n /usr//bin/tar xf ";
    $decompressBin['tar.gz'] = "cd %DEST% \n /usr/bin/tar xzf ";
    ?>

If ``$allowHttpTransfer`` is true, the results of deconvolution can be downloaded through the web interface. If it is false, then the results can only be accessed by other means (e.g. via network shares). Downloaded files are compressed to reduce bandwidth load: ``$compressExt`` defines the type of compression (default is zip).

.. note::

    For the compressed file to be served by the web server, it has to be re-read in. The HRM uses **chunked reading**, that should make sure that even large files can be read without problems. Should the users still encounter problems downloading files from the HRM, then try increasing the value of ``memory_limit`` in ``php.ini``.

**Example:**

.. code-block:: sh

    memory_limit = 128M

.. warning::

    Although HRM takes care of cleaning all temporary files after each download, it may happen that data is left behind if the process fails for any reason. Is is recommended that an HRM admin checks and if necessary cleans the ``${HRM_DATA}/.hrm_downloads`` folder from time to time.


If ``$allowHttpUpload`` is true, an HTTP uploader will be in place to allow for the uploading of the files to be deconvolved through the web interface. Multi-file upload (with directory structures) is indirectly possible by first compressing the files into an archive that the HRM will automatically extract at the end upload process. Default supported formats are ``zip``, ``tgz``, ``tar`` and ``tar.gz`` (as long as the corresponding executables are installed on the system) but more can be added by extending the ``$decompressBin`` array.

.. note::

    The behavior of the HTTP uploader depends on the ``php.ini`` directives ``upload_max_filesize`` and ``post_max_size``, but can also **optionally** be tweaked by the HRM variables ``$max_upload_limit`` and ``$max_post_limit``.   
    
The HTTP uploader uses the ``php.ini`` directive ``upload_max_filesize`` to define the maximum size of each selected file and the ``post_max_size`` directive to define the total upload size allowed in one upload session.
    
The HRM configuration variables ``$max_upload_limit`` and ``$max_post_limit`` can be used to set **more restrictive values** in case the web server runs other services besides HRM. By default, both variables are set to ``0`` so that the values from ``php.ini`` are used.

.. note::

    The HRM administrator can check the values in use in the **System summary** page, under **Configuration**.

**Example:**

.. code-block:: sh

    post_max_size = 2048M
    upload_max_filesize = 1024M

.. note::

    Notice that despite some script executions are relatively fast (like file extraction from zip archives, image previews generation, or SNR estimation), they may take a long time if the images are very large or if deconvolution jobs are already running in the web server. You may need to increase also PHP's ``max_execution_time`` directive in ``php.ini``.

**Example:**

.. code-block:: sh

    max_execution_time = 120

.. warning::

    Although HRM takes care of cleaning all temporary files after each upload, it may happen that data is left behind if the process fails for any reason. Is is recommended that an HRM admin checks and if necessary cleans the ``${HRM_DATA}/.hrm_chunks`` and ``${HRM_DATA}/.hrm_files`` folders from time to time.

.. code-block:: php

    <?php
    ...
    //==============================================================================
    // HRM configuration parameters
    //==============================================================================

    // URL
    $hrm_url = "http://localhost/hrm";

    // Install dir
    $hrm_path = "/var/www/html/hrm";

    // Logging
    // Please create a directory for the logging (default and recommended is /var/log/hrm)
    // and make sure to grant read/write access to the web server user. 
    $log_verbosity = 1;         // 0=quiet, 1=normal, 2=debug
    $logdir  = "/var/log/hrm";
    $logfile = "hrm.log";
    $logfile_max_size = 100;    // maximum size of the logfile in MB
    ?>

The ``$logdir`` variable points to the directory where the log files created by the web server user and the queue manager should reside. Default (and recommended) directory for the logs is ``/var/log/hrm``. Please create this directory and make sure to grant the relevant users read/write access to it!

.. code-block:: php

    <?php
    ...
    // Email
    $send_mail = true;
    $email_sender = "hrm@localhost";
    $email_admin = "hrm@localhost";
    // Comma (',') is the standard separator for lists of email addresses. 
    // Please see: http://tools.ietf.org/html/rfc2822#section-3.6.3
    // Unfortunately, Microsoft Outlook uses semicolon (';') by default and
    // ',' only optionally. Please see: http://support.microsoft.com/kb/820868
    // on how to configure Outlook to support comma-separated lists.
    // If your users are mostly using Outlook, you can tell the HRM to use ';'
    // instead of the standard ',' for distribution lists.
    $email_list_separator = ",";    // Valid options are ',' and ';'.

Enable and configure the e-mail service.

.. code-block:: php

    <?php
    ...
    // Supported authentication types. Possible values are 'integrated', 'active_dir', 'ldap'.
    // These values replace the previous ones (but the old ones are still recognized):
    // 'integrated' replaces 'MYSQL';
    // 'active_dir' replaces 'ACTIVE_DIR';
    // 'ldap' replaces 'LDAP'.
    // You can use more than one authentication mechanism by listing them all in the
    // $authenticateAgainst array below. 
    //
    // e.g. $authenticateAgainst = array("active_dir", integrated");
    // 
    // The first entry in the array is the default authentication mode that will be used
    // for new users. Administrators can then change the authentication mode for individual 
    // users in the user management pages.
    //
    // Make sure to properly configure all authentication modes 
    // (see sample files in config/samples).
    $authenticateAgainst = array("integrated");
    ?>

Setting the authentication mode to **integrated** enables the embedded user management system (independent of the actual database you are using, e.g. postgresql). Use this if you don't have any other user management system in place. Alternatively, simple authentication against **Microsoft's Active Directory** and **OpenLDAP** is possible.

In case one or more of the alternative authentication types are selected (i.e. ``active_dir`` or ``ldap``), some additional configuration will be required (see later).

.. note::

    The super administrator 'admin' always has authentication mode 'integrated'!

.. code-block:: php

    <?php
    ...
    // If true, use DES password encryption; if false, use MD5.
    // This variable is DEPRECATED and will be removed in the next HRM version!
    $useDESEncryption = false;

    // If true, the queue manager and the image processing server run on the same 
    // machine
    $imageProcessingIsOnQueueManager = true;

    // If true the images are copied to the huygens server machine
    $copy_images_to_huygens_server = false;
    ?>

Set ``$imageProcessingIsOnQueueManager`` to false if the queue manager is not on the same machine as the Huygens Core that runs deconvolution.

Set ``$copy_images_to_huygens_server`` to true if the files have to be copied to the machine where the Huygens Core is installed via ssh (using password-less ssh connection!). If Huygens Core has direct access to the file area (e.g. through NFS mount), set this to false.

.. note::

    The use of the variable **$useDESEncryption** is deprecated and will be removed in the next HRM version!

.. code-block:: php

    <?php
    ...
    // Thumbnails require Huygens Core 3.3.2 or higher.

    // Notice that despite some script executions are relatively fast (like
    // thumbnail generation and SNR estimation), they still may take a long time if
    // the images are very large, or if deconvolution jobs are already running in
    // the local server. You may need to increase PHP's max_execution_time
    // directive in php.ini, and restart the web server.

    // If true, allows generates thumbnails and previews for the originals and the
    // results during the deconvolution (i.e. in the computation servers). These
    // are maximum intensity projections (MIP) of the stacks along the main axes,
    // so they provide xy, xz and zy views.
    $useThumbnails = true;

    // If true, allows on-demand generation of a preview of the original images in
    // this web server prior to the deconvolution. For this to work the variable
    // $local_huygens_core must be set correctly above. Notice that not all file
    // formats are readable in a freeware Huygens Core and for full functionality
    // you may need a license string. Otherwise just let the original thumbnails
    // be generated during the deconvolution itself with the previous option.
    // If this is true and the correct version of Huygens is installed, the SNR
    // estimator tools is also enabled (see $enable_code_for_huygens above).
    // This requires $useThumbnails = true;
    $genThumbnails = true;

    // Moreover, if $genThumbnails is true and Huygens 3.5.1 or higher is
    // installed (see $enable_code_for_huygens above), the Signal To Noise ratio
    // can be estimated visually from raw images, in the restoration parameters
    // editor.

    // If larger than zero, generates an AVI movie for 3D stacks that allows
    // browsing along the XY slices, and for time series to browse along MIPs in
    // time. The movie will have this maximum number of pixels in the largest
    // dimension.
    // This requires $useThumbnails = true;
    $movieMaxSize = 300;

    // If true, (and $useThumbnails is also true), it generates not only the MIP
    // previews but also Simulated Fluorescence Process top-view renderings of the
    // original and the restored images (http://support.svi.nl/wiki/SFP).
    $saveSfpPreviews = true;

    // If non-zero, save stack and time series previews of the original and restored
    // data side by side, to allow comparisons. (Requires $useThumbnails and
    // Huygens Core 3.5.2). This is the max size in pixels for each of the images's
    // slicer.
    $maxComparisonSize = 300;

These were several options for preview generations.

.. code-block:: php

    <?php
    ...
    // A shell command that executes ping four times and stops afterwards
    $ping_command = 'ping -w 4';    // use this on linux systems
    // $ping_command = 'ping -t 4'; // use this on macosx systems
    // $ping_command = 'ping';  // use this on cygwin

    // The parameter for the ping command after the hostname
    $ping_parameter = '';           // use this on linux systems
    //$ping_parameter = '56 4'; // use this on cygwin
    ?>

This is used by the queue manager to test whether the processing machine is reachable.

.. note::

    In HRM it is possible to use a machine for each of the components, i.e. web server, database server, one or more processing machines, file server and queue manager. Configuration files are needed only on the web server and the machine running the queue manager. Make sure to fill the various path and user fields from the perspective of the machine that hosts each of the configuration files!
