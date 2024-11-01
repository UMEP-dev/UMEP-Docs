.. _LandCoverReclassifier:

Urban Land Cover: Land Cover Reclassifier
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Contributor
   .. list-table::
      :widths: 50 50
      :header-rows: 1

      * - Name
        - Institution
      * - Fredrik Lindberg
        - Gothenburg


* Introduction
     The Land Cover Reclassifier is a simple plugin that can be used to create a UMEP land cover raster grid. The land cover fractions included in UMEP are:

.. list-table::
   :widths: 10 25 75
   :header-rows: 0

   * - 1
     - Paved
     - Paved surfaces (e.g. roads, car parks)
   * - 2
     - Buildings
     - Building surfaces
   * - 3
     - Evergreen Trees
     - Evergreen trees and shrubs
   * - 4
     - Deciduous Trees
     - Deciduous trees and shrubs
   * - 5
     - Grass
     - Grass surfaces
   * - 6
     - Bare soil
     - Bare soil surfaces and unmanaged land
   * - 7
     - Water
     - Open water (e.g. lakes, ponds, rivers, fountain)


* Dialog box
        .. figure:: /images/Landcoverreclassifier.jpg
            :align: center
            :width: 75%

            The dialog for the Land Cover Reclassifier

* Dialog sections
   .. list-table::
      :widths: 10 90
      :header-rows: 0

      * - upper
        - Select raster land cover dataset to be reclassified into the UMEP land cover classes
           - **Include additional land cover classes used in TARGET**: If this is ticked in, two more classes appear that is used in the `TARGET` tool.
      * - middle
        - Choose interval values to be classified into a certain UMEP land cover class.
           - Not all lines and boxes need to be filled in, but multiple lines are available in case many different intervals are to be classified as the same land cover class.
      * - lower
        - Specify the output file (.tiff) etc.

* Input raster
     Any valid raster dataset (float or integer) loaded into QGIS will appear in this dropdown list. Choose the one that includes your land cover information.
     
* Include additional land cover classes used in TARGET
     If this is ticked in, two more classes appear that is used in the `TARGET` tool. TARGET land cover infromation is in somewhat different classes that the standard UMEP classes. The updated Land Cover Reclassifier includes possibilities to pre-process data into all nine classes used by TARGET. In the table below you see the classes used and how they relate to the standard UMEP classes:

    .. list-table::
       :widths: 20 20 60
       :header-rows: 1

       * - TARGET class
         - UMEP class
         - Comment
       * - roof
         - buildings
         -  
       * - road
         - paved
         - Total impervious surface in UMEP 
       * - watr
         - water
         -  
       * - conc
         - NA
         - Part of paved. Impervious in TARGET is both divided up between road and concrete. 
       * - Veg
         - Conifer and Deciduous trees
         - TARGET only have on class of trees whereas UMEP as two.
       * - dry
         - grass
         - TARGET divides grass into two classes either dry or completely wet.
       * - irr
         - grass
         - TARGET divides grass into two classes either dry or completely wet.
       * - NA
         - bare soil
         - TARGET has no bare soil cless. Bare soil becomes dry grass if UMEP land cover is used.

* Land cover classes
     Fill the interval values that you want to reclassify into a certain cover class. All values not included will appear as 0 in the output land cover raster. This should be avoided.

* Output file
     Location and filename (geoTIFF) are specified here.

* Run
     Starts the reclassification.

* Close
     Closes the plugin.
