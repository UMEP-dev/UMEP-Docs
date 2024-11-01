.. _SUEWSDatabasePrepare:

Urban Energy Balance: SUEWS Database Prepare
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: **UPCOMING PLUGIN**: This plugin is still experimental or non-existing. Please report any issues to our `code repository <https://github.com/UMEP-dev/UMEP>`__.

* Contributor:
    .. list-table::
       :widths: 50 50
       :header-rows: 1

       * - Name
         - Institution
       * - Oskar Bäcklin
         - Gothenburg
       * - Fredrik Lindberg
         - Gothenburg
       * - Ting Sun
         - London
       * - Sue Grimmond
         - Reading

* Introduction:
    The pre-processor *SUEWS Prepare Database* make use of the database used in `SUEWS Database Manager <SUEWSDatabase>` to generate surface-related input data from geographical data for `SUEWS <SUEWSAdvanced>`, the Surface Urban Energy and Water Balance Scheme (`Järvi et al. 2011 <https://www.sciencedirect.com/science/article/pii/S0022169411006937?via%3Dihub>`__). SUEWS (`link to manual <https://suews.readthedocs.io/en/latest/>`__) simulates the urban radiation, energy and water balances using commonly measured/modelled meteorological variables and information about the surface cover. It utilizes an evaporation-interception approach (`Grimmond and Oke 1991 <https://agupubs.onlinelibrary.wiley.com/doi/10.1029/91WR00557>`__), similar to that used in forests, to model evaporation from urban surfaces. The surface state for each surface type at each time step is calculated from the running water balance of the canopy where the evaporation is calculated from the Penman-Monteith equation. The soil moisture below each surface type (excluding water) is also taken into account.
    
    This plugin make use of information generated from other plugins listed below.
    
* Related Preprocessors, Processors and Postprocessors
   `MetPreprocessor`, `LandCoverFraction(Grid)`, `MorphometricCalculator(Grid)`, `SUEWSDatabase`, `ERA5`, `SUEWSAdvanced`, `SUEWSAnalyser`

* Dialog box：
    .. figure:: /images/SUEWS_DBPrepare_main.jpg
        :width: 100%
        :align: center

        The Dialog for SUEWS Database Prepare. *Click on image for enlargement*.


* Vector data:
    Various vector data used in this tool, some required and some optional. Any vector file format compatible with QGIS is possible, however, it is recommended to use the shape-file format.
    
    * Vector grid (polygon):
        Here the grid polygon layer should be specified. This defines the model domain and the grid size. Same layer should be used that was used in previous tools e.g., `LandCoverFraction(Grid)` etc. 
    
    * ID field:
        Choose an attribute from the selected polygon layer that will be used to separated the different polygon objects from each other. An attribute field of unique numbers or letters should be used.
        
    * Population density:
        This data needs to be added through the polygon grid attribute table. Make sure that the data exist as an attribute field and select it in the drop down menu. Tick in *Include daytime working population (optional)* if you have that information in a separate attribute.
        
    * Use Urban typology layer from SUEWS Database Manager (optional)
        Specify a polygon layer created from the `SUEWS Database Prepare <SUEWSDatabasePrepare>` plugin. Urban typologies  represents certain properties for specific urban neigborhoods. Information (e.g. albedo) from this polygon layer is then aggregated based on the vector grid specified above. If this option is not ticked in, a defaut building typology from the database is required.
    * Use Street network to estimate traffic intensity (optional)
        This option is not yet active (work in progress). Here is will be possible to add more specific infromation on traffic for each grid, either by using a vector line layer supplied by the user or exploiting Open Street Map data to estimate traffic intensity
        
* Raster data:
    The raster digital surface models are used for two purposes in this plugin, 1: when aggregating between urban typology layer and vector grid layer and 2: if vertical morhology (Spartacus) is calculated.

    * Building and ground DSM:
        A raster DSM (e.g. geoTIFF) consisting of ground and e.g. building height (metres above sea level).

    * Raster DEM
        A DEM (e.g. geoTIFF) consisting of pixels with ground heights (metres above sea level).

* Daylingt savings, UTC and Initial Conditions:
    Here, some general settings are made for the SUEWS model.
    
    * Day light savings:
        The plugin needs to have access to the correct days in which the switches to and from daylight savings time occurs in the region. The numbers in the text boxes represent the `days of year <https://landweb.modaps.eosdis.nasa.gov/browse/calendar.html>`__. For example, the 21st of January is day of year 21 and the 2nd of February is day of year be 33 and so on. Make sure the days in the text boxes for daylight savings time in the main settings tab are correct for `your region <https://en.wikipedia.org/wiki/Daylight_saving_time_by_country>`__.
        
    * UTC:
        Time zone needs to be specified. Positive numbers moving east (e.g. Stockholm UTC +1). This is related to the meteorological forcing data so if ERA5 data is used, UTC should be equal to zero.
        
    * Initial conditions:
        The initial conditions are entered here. These relate to time of year, days since rain, soil moisture state and daily mean air temperature at the beginning of a model run. The state of the leaf cycle sets a rough estimate of leaf area index based on season. 
        
* Meteorological forcing data:
    The location and filename (.txt) of the meteorological file should be specified here. The format used in most UMEP-related plugins where meteorological data is required can be generated using the Metdata Processor in UMEP. For details, see the help section in the Metdata Processor or the SUEWS manual
    
* Data for land cover fractions, building morphology and tree morphology：
    To use SUEWS land cover and morphology data for buildings and vegetation are needed. This information can be acquired through other plugins in UMEP. This data can then be added into this plugin by importing the data as text files. The text files on land cover and morphology are generated with the Land Cover Fraction plugin and the Image Morphometric Calculator, respectively. Alternatively, the data need to be available in the attribute table of the polygon layer. If the data are available in this format simply check the check boxes below the buttons to change the interface from buttons into drop down menus. In the drop down menus select the correct attribute fields for the data and the selection is done. 
    
* National parameters:
    Here, you specify the country that you want to model. The plugin retrieves information from the database and specifies the setting suitable for the country choosen for each land cover class. You can also choose another land cover setting for each class. If you like to see the settings for a specific land cover class, go to the land cover-tab in `SUEWS Database Manager <SUEWSDatabase>`.

* Profiles:
    Here, different diurnal profiles, based on the country choosen is set. The plugin retrieves information from the database and specifies the profile settings suitable for the country choosen. You can also choose another profile setting for each profile type. If you like to see the settings for a specific profile, go to the profile-tab in `SUEWS Database Manager <SUEWSDatabase>`.

* Vertical morphology (Spartacus) (optional):
    This panel is used to populate information used by the Sparacus scheme in SUEWS. This is a new option that is still under development. More info is coming

* Output folder:
    Location where the converter data should be stored. 

* Generate:
    Starts the process of generating all the data.

* Close:
    Closes the plugin.