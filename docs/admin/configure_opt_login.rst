.. include:: global_directives.inc

.. toctree::
   :maxdepth: 1

************************
Customize the login page
************************

You can customize the login page by renaming the ``$HRM_USER/login_user.inc.sample file`` into ``$HRM_USER/login_user.inc`` and adding information that you would like to appear on the HRM login page, such as contact information, quick instructions, etc.

.. warning::

    Please use valid HTML code: no validation is performed on your ``$HRM_USER/login_user.inc`` HTML code, and you are responsible for any vulnerability you introduce into the HRM!

Example
-------

.. code-block:: html

    <h2>Contact information</h2>
    <ul>
        <li><a href="mailto:admin@facility.edu?Subject=Help!">HRM admin</a></li>
    </ul>

    <h2>HRM custom instructions</h2>
    <ul>
        <li><a href="http://www.facility.edu/hrm_instr.pdf">Using the HRM at our facility</a></li>
    </ul>

With a bit of HTML and CSS skills you can make your login page shine!
