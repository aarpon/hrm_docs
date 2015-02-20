Documentation for the HRM
=========================

This repository contains the sources of the [sphinx-based][1] documentation for the [Huygens Remote Manager][2]. It consists of two parts:

* the admin instructions (in `docs/`)
* the user manual (in `usermanual/`)

The compiled documentation is available on [readthedocs.org][3] as HTML, PDF and Epub.

[1]: http://sphinx-doc.org/ "Sphinx"
[2]: https://github.com/aarpon/hrm "Huygens Remote Manager"
[3]: http://huygens-remote-manager.readthedocs.org "Read the Docs"


Editing conventions
===================

1.- When creating HRM screenshots log on to HRM with the user 'hrmuser', then
capture the screenshot. This way all the HRM screenshots in the manual will
display the same user.

2.- Save image as .PNG. Currently there are many .gif which are only meant as
a guide. Gif images will be replaced by png's.


Building the documentation using a local sphinx readthedocs (RTD) theme
=======================================================================

Theme Installation
------------------

Install the sphinx RTD theme with:

    (sudo) pip install sphinx_rtd_theme

To upgrade it, use:

    (sudo) pip install --upgrade sphinx_rtd_theme

Building the docs
-----------------

Set the environment variable `USE_LOCAL_SPHINX_RTD_THEME` to enable the local sphinx_rtd_theme. You can set it in `~/.bashrc` or `~/.bash_profile` or define it right before use:

    export USE_LOCAL_SPHINX_RTD_THEME=1
    make html

The configuration file `conf.py` will fall back to the default theme if sphinx_rtd_theme is not found.
