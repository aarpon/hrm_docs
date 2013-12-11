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
    
