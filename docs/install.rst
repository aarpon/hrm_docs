.. include:: global_directives.inc

.. toctree::
   :maxdepth: 3

***************
Install the HRM
***************

Download or checkout the HRM as explained :ref:`here <download-hrm>`.

Unpack the downloaded archive to web server document root directory ($ROOT). This is the directory where Apache2 finds the html and php files to serve.

.. code-block:: sh

    $ sudo tar xjvf hrm_x.y.z.tar.bz2 $ROOT

where ``x.y.z`` is a placeholder for the HRM version.

+----------+-------------------------------+
| OS       | $ROOT                         |
+==========+===============================+
| Ubuntu   | /var/www; /var/www/html       |
+----------+-------------------------------+
| Fedora   | /var/www/html                 |
+----------+-------------------------------+
| SuSE     | /srv/www/htdocs               |
+----------+-------------------------------+
| Mac OS X | /Library/WebServer/Documents  |
+----------+-------------------------------+

.. note::

    You can of course extract or clone the HRM somewhere else: just add the location to the Apache2 configuration (``httpd.conf``).
