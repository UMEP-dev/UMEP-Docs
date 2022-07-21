.. _VectorGenerator:

Spatial Data: Vector Data Generator
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Contributor:
   .. list-table::
      :widths: 50 50
      :header-rows: 1

      * - Name
        - Institution
      * - Jérémy Bernard
        - Gothenburg
      * - Fredrik Lindberg
        - Gothenburg

* Introduction
    Some processors need building and vegetation vector data as input (e.g. URock). This plugin convert Raster grids (DEM, DSM and CDSM) + building footprint to building and vegetation vector data with height attribute. For the vegetation, you can also provide points data (trunk location) and radius and / or height to create the vegetation footprint with height attribute.

* Related processors
   `URock`

* Dialog box
   .. figure:: /images/VectorGenerator_v2022a.png
      :width: 100%
      :align: center

      The processing dialog for the Vector generator. Click on image for enlargement.

* Input parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Building footprint (optional)
        - Spatial input data containing buildings footprint as vector data
      * - Building raster DSM (3D objects + ground or only 3D objects) (optional)
        - A DSM consisting of ground and building heights (in this case you should provide a DEM) or building height only.
      * - DEM (ground - only if building DSM is 3D objects + ground) (optional)
        - A DEM
      * - Vegetation raster DSM (3D canopy) (optional)
        - A DSM consisting of pixels with vegetation heights above ground. Pixels where no vegetation is present should be set to zero.
      * - Vegetation point data (trunk location and max height) (optional)
        - Vector file containing points for each tree trunk and at least an attribute for tree top height or for tree crown radius
      * - Vegetation height field (optional)
        - Name of the attribute used to store the maximum height of the tree
      * - Horizontal vegetation radius field (optional)
        - Name of the attribute used to store the horizontal radius of the tree
      * - Tree height / tree crown radius ratio used if either height or radius value is missing (optional)
        - Aspect ratio (height / horizontal radius) value used for all trees if height and radius are not given for all trees (default 0.75) 
      * - Attribute name for building height in output data (optional)
        - Name of the attribute expected in the output building vector file (default 'ROOF_HEIGHT')
      * - Attribute name for vegetation height in output data (optional)
        - Name of the attribute expected in the output vegetation vector file (default 'VEG_HEIGHT')
      * - Output building vector file (geojson or shp)
        - Where you want to save the building output file
      * - Output vegetation vector file (geojson or shp)
        - Where you want to save the vegetation output file
 

* Remarks
      -  The Raster and vector files should have a projection with meters as units.
