.. _TARGETPrepare:

Urban Heat Island: TARGET Prepare
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: This plugin is still experimental. Please report any issues to our `code repository <https://github.com/UMEP-dev/UMEP>`__.


* Contributor:
    .. list-table::
       :widths: 50 50
       :header-rows: 1

       * - Name
         - Institution
       * - Fredrik Lindberg
         - Gothenburg

* Introduction:
    **TARGET** (The Air-temperature Response to Green blue-infrastructure Evaluaition Tool) is a simple modelling framework used to examine intra urban climate (10\ :sup:`2` m resolution). It has specifically been developed as an efficient, easy-to-use model albe to investigate heat mitigation effects of green and blue infrastructure within urban areas but can also be used to model the canopy urban heat island (`Broadbent et al. 2019) <https://gmd.copernicus.org/articles/12/785/2019/>`__ 
    
    The pre-processor TARGET Prepare can be used to prepare input data for the `TARGET in UMEP <TARGET>` or elsewhere. This plugin generates a **TARGET**-formatted land cover file for each area that should modelled as well as the directory system that is used by the model. 

* Related Preprocessors, Processors and Postprocessors
   `LandCoverFraction(Grid)`, `MorphometricCalculator(Grid)`, `TARGET`, `TARGETAnalyser`

* Dialog box:
    .. figure:: /images/TARGETPrepareInterface.jpg
        :width: 75%
        :align: center

        Dialog for the TARGET Prepare plugin. Click on image for enlargement.

* Parameters:

   .. list-table::
      :widths: 25 75
      :header-rows: 0
      
      * - Polygon grid
        - A vectory polygon grid that depicts the modelling area(s). This should be the same polygon layer that was used in `TARGET`. The **ID field** should an attribute field with unique numbers, preferably intergers.
      * - Building morphology file (.txt)
        - Specify a text file on building morphology that are generated with the `Image Morphometric Calculator <MorphometricCalculator(Grid)>` plugin. Use the isotropic text file (*prefix*_IMPGrid_isotropic.txt).
      * - Land cover fractions file (.txt)
        - Specify a text file on land cover fractions generated with the `Land Cover Fraction <LandCoverFraction(Grid)>` plugin. Use the isotropic text file (*prefix*_LCFG_isotropic.txt).
      * - Use standard UMEP land cover grid (fractions below is used)
        - TARGET make use of 9 different land cover classes. Other UMEP related tools such as SUEWS make use of 7 classes (Paved, Buildings, Evergreen Trees, Deciduous Trees, Grass, Bare soil and Water) which are the same for TARGET, but added are also Concrete and Irrigated grass. To make it possible to use 'standard' UMEP land cover grids, this tick box make it possible to divide the paved and grass land covers into paved/concrete and grass/irrigated grass based on the fractions below. If this tick box is un-ticked, 9 classes will be considered. Then the `Land Cover Fraction <LandCoverFraction(Grid)>` plugin requires 9 classes in the land cover grid used. 
      * - Site name
        - Here you specify a name that will be used in the folder system later used for the TARGET-model. Only use regular letters (not spaces etc.).

* Ourput folder:
    Directory where generated files will be stored. 

* Run:
    Starts the process.

* Help
    Link to this manual page.

* Close:
    Closes the plugin.
