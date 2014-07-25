Using a local sphinx readthedocs (RTD) theme
============================================

Installation
------------

Install the sphinx RTD theme with:

    $ (sudo) pip install sphinx_rtd_theme

To upgrade it, use:

    $ (sudo) pip install --upgrade sphinx_rtd_theme

Usage
-----

Set the environment variable 'USE_LOCAL_SPHINX_RTD_THEME' to enable the local sphinx_rtd_theme. You can set it in ~/.bashrc or ~/.bash_profile or define it right before use:

    $ export USE_LOCAL_SPHINX_RTD_THEME=1; make html

The configuration file conf.py will fall back to the default theme if sphinx_rtd_theme is not found.
    


HRM Manual: editor conventions
=================================

1.- When creating HRM screenshots log on to HRM with the user 'hrmuser', then
capture the screenshot. This way all the HRM screenshots in the manual will
display the same user.

2.- Save image as .PNG. Currently there are many .gif which are only meant as
a guide. Gif images will be replaced by png's.
