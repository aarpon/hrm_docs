.. include:: global_directives.inc

*****************
Export data share
*****************

The HRM offers data upload and download through the broswer. For large datasets, however, it is recommended to set up more performant ways to get data in and out of the HRM file server.

One approach consists of exporting the ``$HRM_DATA`` folder as a samba share. See for instance `here <https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html>`_ on how to setup samba.

What follows is a sample configuration for exporting the ``$HRM_DATA`` folder (add it to the ``/etc/samba/smb.conf`` file):

.. code-block:: sh

    [hrm_data]
        comment = HRM data folder
        path = /data/hrm_data
        force user = hrm
        force group = hrm
        writeable = Yes
        create mask = 0666
        directory mask = 0777
        guest ok = No
        strict locking = no
