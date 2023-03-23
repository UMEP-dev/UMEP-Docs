.. _SpatialTC:

Outdoor Thermal Comfort: Spatial Thermal Comfort
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* Contributor
   .. list-table::
      :widths: 50 50
      :header-rows: 1

      * - Name
        - Institution
      * - Fredrik Lindberg
        - Gothenburg

* Introduction
    The **Spatial TC** plugin can be used to make maps of thermal indicies making use of output from the `SOLWEIG <SOLWEIG>`-plugin and the `URock <URock>`-plugin. All prior tools need to be executed via the Processing toolbox in QGIS and no filenames and folder structures should be changed. The Meteorological forcing file should be the same as used when executing SOLWEIG. This file can be found in the output-folder from SOLWEIG (*metforcing.txt*).

* Dialog box
    .. figure:: /images/SpatialTC.jpg
        :width: 100%
        :align: center

        Dailog for Spatial TC


* Basic parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0
      
      * - Mean radiant temperature raster (SOLWEIG)
        - A raster grid originating from a SOLWEIG run. Filename should not be changed (*Tmrt_YYYY_DOY_HHMMD.tif*).
      * - Pedestrian wind speed raster
        - A raster grid originating from a URock run.
      * - Raster to exclude building pixels from analysis
        - A raster grid originating from a SOLWEIG run. This is created if the tickbox specifying the building grid output is ticked in.
      * - Input meteorological tile (.txt). Same as used for Tmrt map.
        - Meterological forcing data used in the SOLWEIG run. This file can also be found in the output folder from a the SOLWEIG run executed via the Processing Toolbox in QGIS.
      * - Thermal Index to map
        - Here, a specific thermal index can be choosen. At the moment, PET is only available. More is coming!

* Advanced Parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Age (yy)
        - Used to calculate PET.
      * - Activity (W)
        - Used to calculate PET.
      * - Clothing (clo)
        - Used to calculate PET.
      * - Weight (kg)
        - Used to calculate PET.
      * - Height (cm)
        - Used to calculate PET.
      * - Sex
        - Used to calculate PET.
    
* Remarks
    - The wind speed and direction columns found in the meteorological forcing data does not have to be the same used in URock. These column are used if PET or UTCI is calculated for Point of Interests (POI).
    - All rasters used must have the same sixe. This can be accomplished by setting the URock output to be the same size as the SOLWEIG output.