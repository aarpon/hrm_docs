.. include:: global_directives.inc

.. _step4:

Analysis parameters (4/5)
=========================

In step 4 - |AnalysisParameters22x22| **Analysis Parameters** - the analysis
settings for your images can be specified and saved. As always, the analysis parameters are grouped in templates. A parameter template can be reused in future deconvolution and analysis jobs.
This will be useful when the same type of analysis has to be performed on other images. Moreover, the parameter templates can be shared among HRM users,
fostering collaboration and re-usage of good analysis settings.


Notice that the following selections are possible at this stage:

* **Admin analysis templates**: parameter templates created by the HRM administrator to be used as references. They can be copied and edited by the HRM users. In   order to use them, they first need to be copied to **Your analysis templates** by using |DownArrow22x22|.
   
* **Your analysis templates**: the analysis templates the user can actually use directly. All templates in this area may be selected, edited, removed, etc.

* **New/clone analysis template**: entry field for the name of a new parameter
  template. First type a name for the new template and click on
  |CreateTemplate22x22|. A new template will be created. HRM will present you
  with empty template parameters so that meaningful values can be assigned
  to them.


.. note:: Notice that |CreateTemplate22x22| |EditTemplate22x22|
          |CloneTemplate22x22| |ShareTemplate22x22| |FavouriteTemplate22x22|
          |DeleteTemplate22x22| show tooltips stating their action w.r.t
          templates. Namely, **create**, **edit**, **clone**, **share**,
          **mark as favourite** and **delete**.

An analysis parameter template consists of a number of options that provide Huygens Core with information about the type of analysis to execute on your images. To get a **preview** of the template contents select the template, the contents will be displayed on the right panel.

.. note:: When editing a template help links |HelpLink22x22| are displayed at
          key locations to point you to specific articles of the SVI-wiki.

The following parameters can be edited in a template.

.. toctree::
   :maxdepth: 3

   step4_colocalization
   step4_channels
   step4_coloccoefficients
   step4_threshold
   step4_colocmaps
   
             
