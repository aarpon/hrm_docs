.. include:: global_directives.inc

.. _script_install_hrm_files:


The HRM files
=============

The different versions are fetched directly from GitHub. You can choose the one you want to
install. Master will normally be hidden unless ‘--rolling=true’ is specified as a command line
argument. Normally, you would want a known starting point (a version point), unless some rolling
fixes need installing. Should you choose to install from a zip file, the option is also given
in the menu:

|script_install_hrm_files_1|

You may be asked to enter a token (composer)

.. note::
   Could not fetch
   https://api.github.com/repos/zindy/php-traditional-server/contents/composer.json?ref=master,
   please create a GitHub OAuth token to go over the API rate limit
   Head to https://github.com/settings/tokens/new?scopes=repo&description=Composer+on+d9+2018-12-06+1210 to retrieve a token. It will be stored in "/root/.composer/auth.json" for future use by
   Composer.
   Token (hidden):

In which case, follow the link, enter your password and generate a personal access token.
Paste it, then you should see the following message:

.. note::
   Token stored successfully.
   Updating dependencies

   
If you select zip:

|script_install_hrm_files_2|

If you select any of the other tags then do git clone into $hrmdir or if the git repository is
already present then do a git fetch.

Image folder

|script_install_hrm_files_3|

In case the folder already exists, we need to ensure the hrm group can read and write to it.
For that we recursively change the permissions on the folder. This is only something we allow
in interactive mode and warn the user about the consequences of doing so.

|script_install_hrm_files_4|

In case the user errs on the side of caution, the following dialog message is displayed:

|script_install_hrm_files_5|
