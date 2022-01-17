.. include:: global_directives.inc

.. _script_install_non_interactive:


Non interactive mode
====================

Execute the installation script from the command line, as follows:

.. code-block:: sh
		
   user@hrm ~/hrm_installer$ sudo ./setup.sh --interactive=false
   [sudo] password for user:

HRM will be installed automatically. Output similar to this should be displayed:
		
.. code-block:: sh
		
   Using mysql as DBMS.
   The HRM database host is: localhost
   The HRM database name is: hrm
   The username for the HRM database is: hrmuser
   The password for the HRM user is: pwd4hrm
   The database hrm already exists.
   The user hrmuser already exists.
   The system user which will run HRM is: hrmuser
   The system group for hrmuser is: hrm
   HRM will run with:
   uid=998(hrmuser) gid=999(hrm) groups=999(hrm)
   The HRM installation directory is: /var/www/html/hrm
   The /var/www/html/hrm folder will be automaticaly updated
   The $hrmtag is now 3.5.0
   /var/www/html/hrm already contains the git repository.
   README.md oops.txt scripts setup.sh setup.sh~ test_dialog.sh test_dialog.sh~ ~ 3.5.0
   warning: refname '3.5.0' is ambiguous.
   
   composer.lock
   composer.phar
   Already on '3.5.0'
   Set up HRM for release **IN PLACE**... /var/www/html/hrm/setup/../
   You are already using composer version 1.7.3 (stable channel).
   Do not run Composer as root/super user! See https://getcomposer.org/root for details
   Loading composer repositories with package information
   Updating dependencies
   Generating autoload files
   Enter PHP post_max_size (limits POST size for browser uploads)
   Enter PHP upload_max_filesize (limits file size for browser uploads)
   Initialized database revision to 0.
   Needed database revision for HRM v3.5 is number 16.
   Current database revision is number 0.
   Updating...
   Database successfully updated to revision 1.
   Database successfully updated to revision 2.
   Database successfully updated to revision 3.
   Database successfully updated to revision 4.
   Database successfully updated to revision 5.
   Database successfully updated to revision 6.
   Database successfully updated to revision 7.
   Database successfully updated to revision 8.
   Database successfully updated to revision 9.
   Database successfully updated to revision 10.
   Database successfully updated to revision 11.
   Database successfully updated to revision 12.
   Database successfully updated to revision 13.
   Database successfully updated to revision 14.
   Database successfully updated to revision 15.
   Database successfully updated to revision 16.
   Configuring HRM queue manager to start at boot
   Configuring startup for init system type 'sysv'.
