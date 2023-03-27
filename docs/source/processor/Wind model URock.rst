.. _URock:

Urban Wind Fields: URock
~~~~~~~~~~~~~~~~~~~~~~~~
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
      * - Sandro Oswald
        - Vienna (ZAMG)

* Introduction
    The **URock** plugin can be used to calculate spatial variations of wind speed and wind direction in 3 dimensions using 2.5D building and vegetation data. The methodology originates from Röckle (1990), has been implemented in proprietary softwares such as QUIC-URB (Brown et al., 2013) or SkyHelios (Fröhlich and Matzarakis, 2018) and is further described in (Bernard et al., 2023 - not published). The current version of the model is 2023a.

* Related Preprocessors
   `MetPreprocessor`, `ERA5`, `URockPrepare`

* Dialog box
   .. figure:: /images/URock_v2023a.png
      :width: 100%
      :align: center

      The processing dialog for the URock model. Click on image for enlargement.

* Input parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Building polygons
        - Spatial input data containing buildings as 2.5D vector data
      * - Building height field
        - Name of the attribute used to store building height (considered as flat roof)
      * - Vegetation polygons (optional)
        - Spatial input data containing buildings as 2.5D vector data
      * - Vegetation crown top height (optional)
        - Name of the attribute used to store the height of the top of the vegetation crown
      * - Vegetation crown base height (optional)
        - Name of the attribute used to store the height of the bottom of the vegetation crown (the default is set to 25% of the crown top height)
      * - Vegetation wind attenuation factor (optional)
        - Name of the attribute used to store the vegetation factor attenuation (the default is set to 1.00 - Larch plantation - for more values refer to Cionco et al. (1978))
      * - Vertical wind profile file (.csv) (optional)
        - Text file containing the vertical wind profile. It consists in two columns and no header: 1st column contain measurement height (m), 2nd column the corresponding wind speed (m/s)
      * - Vertical wind profile type (optional)
        - If the wind profile file is not provided, need to set a vertical wind profile type and a reference wind height and speed (default 'power' law)
      * - Height of the reference wind speed (m) (optional)
        - If the wind profile file is not provided, need to set a vertical wind profile type and a reference wind height and speed (default 10 m)
      * - Wind speed at the reference height (m) (optional)
        - If the wind profile file is not provided, need to set a vertical wind profile type and a reference wind height and speed (default 2 m/s)
      * - Wind direction (° clock-wise from North)
        - Main wind direction within the urban canopy (default 45°)
      * - Raster to use as output (optional)
        - Limit the URock calculation to the raster extend and interpolated output to the raster grid 
      * - Horizontal resolution (m) (optional)
        - Grid resolution used along horizontal axes (default 2 m). If you want the raster resolution to be used, leave this cell blank.
      * - Vertical resolution (m)
        - Grid resolution used along the vertical axis (default 2 m)
      * - Output wind height (m) - if several values, separated by ','
        - The horizontal variation of wind speed and wind direction can be saved for a given height / list of height (default only 1.5 m)
      * - String used as output base name
        - Name of the output file without extension (default urock_output)
      * - Save 2D wind speed as raster file(s)
        - For each height specified in 'Output wind height', the horizontal variation of the wind speed is saved in a raster file
      * - Save 2D wind field as vector file(s)
        - For each height specified in 'Output wind height', the horizontal variation of the wind field is saved in a vector file
      * - Save 2D wind speed in a NetCDF file
        - Save the URock output in a NetCDF file split into two groups containing: (i) 3D wind field for the whole domain, (ii) the vertical wind speed profile used as input
      * - Java environment path (should be set automatically)
        - Java is used for some calculation and Python needs to know what is the Java environment path on your computer (a default value should be identified automatically)
      * - Directory to save the outputs
        - A folder path where will be saved the output files

* Quick example on how to run URock
             #. Download the (`Göteborg test dataset <https://urban-meteorology-reading.github.io>`__).
             #. Add the raster layers (DEM, DSM, and CDSM) and the building vector (buildings.shp) from the Goteborg folder into a new QGIS session. The coordinate system of the rasters is **Sweref99 1200 (EPSG:3007)**. Please verify that it is the case. If not, save it with this coordinate system.
             #. In order to run URock, some additional datasets must be created based on the raster grids and vector layer you just added. Open the 'URock Prepare' module from the UMEP Pre-processor and create building and / or vegetation vectors using DEM, DSM and buildings vector for buildings and CDSM for vegetation. Leave all other settings as default. Two layers should be created at the end of this preprocess: 'Building with height' and 'Vegetation with height'.
             #. Now you are ready to generate your first wind maps. Open URock and use the settings as shown in the figure below but replace the paths to fit your computer environment (Java environment path should be set automatically, do not modify this one). When you are finished, press *Run*.

.. figure:: /images/URockfirsttry.png
   :width: 100%
   :align: center

   Setting for a first try with the URock model. Click on image for enlargement.
 

* Remarks
      -  This plugin is computationally intensive i.e. large grids will take a lot of time and very large grids (more than 30'000'000 3D grid cells) will not be possible to use.
      -  URock consider building roofs as flat, thus do not trust wind speed near roofs if your building roof is normally not flat.

* References
      - Bernard, Jérémy, Fredrik Lindberg, and Sandro Oswald. Urban wind field calculation through the Röckle based method: the basics for a GIS implementation. No. EMS2021-27. Copernicus Meetings, 2021. 
      - Brown, Michael J., Akshay A. Gowardhan, Mathew A. Nelson, Michael D. Williams, et Eric R. Pardyjak. « QUIC transport and dispersion modelling of two releases from the Joint Urban 2003 field experiment ». International Journal of Environment and Pollution 52, nᵒ 3‑4 (1 janvier 2013): 263‑87. https://doi.org/10.1504/IJEP.2013.058458.
      - Fröhlich, Dominik, et Andreas Matzarakis. « Spatial Estimation of Thermal Indices in Urban Areas—Basics of the SkyHelios Model ». Atmosphere 9, nᵒ 6 (juin 2018): 209. https://doi.org/10.3390/atmos9060209.
      - Rockle, R. "Bestimmung der Stomungsverhaltnisse im Bereich komplexer Bebauungsstrukturen der Technischen Hochschule Darmstadt Germany." (1990).
