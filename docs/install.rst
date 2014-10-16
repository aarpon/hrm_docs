.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

***************
Install the HRM
***************

Download or checkout the HRM as explained :ref:`here <download-hrm>`.

Unpack the downloaded archive to web server document root directory. This is the directory where Apache2 finds the html and php files to serve.

|ubuntu| up to **13.10**

.. code-block:: sh

    sudo tar xjvf hrm_x.y.z.tar.bz2 -C /var/www

|fedora| and |ubuntu| **14.04 LTS** and later

.. code-block:: sh

    sudo tar xjvf hrm_x.y.z.tar.bz2 -C /var/www/html

where ``x.y.z`` is a placeholder for the HRM version.

.. note::

    You can of course extract or clone the HRM somewhere else: just add the location to the Apache2 configuration (``httpd.conf``).
