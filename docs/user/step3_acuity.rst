.. include:: global_directives.inc

.. _acuity:

Acuity
======

As of HRM 3.8 the acuity parameter **controls the sharpness of the result**.

In older Huygens and HRM versions this could be controlled by setting lower
or higher than expected :ref:`signal_to_noise_ratio` values for the image.

If you would like to keep working like in the older versions simply set the
acuity mode to **legacy**:

|Acuity1|

For integrating the acuity parameter in your workflows and to leave the
legacy mode behind enable the acuity mode and set acuity values for each
channel. The accepted values range between -100 and +100.

|Acuity2|

* **Positive acuity**: the more positive the acuity, the
  sharper the result and the less noise suppression (or potentially noise
  amplification).

* **Negative acuity**: the more negative the acuity, the more noise suppression
  and the less sharpness.






