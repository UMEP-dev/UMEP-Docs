.. _SUEWSadvanced:

Urban Energy Balance: Urban Energy Balance (SUEWS, advanced)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* Contributor
   .. list-table::
      :widths: 50 50
      :header-rows: 1

      * - Name
        - Institution
      * - Fredrik Lindberg
        - Gothenburg

* Introduction
     - This plugin makes it possible to run the Surface Urban Energy and Water Balance Scheme (SUEWS). SUEWS is also available as a separate program and a simplified version within UMEP (SUEWS Simple).
     - SUEWS (Järvi et al. 2011, 2014, Ward et al. 2016a, b) simulates the urban radiation, energy and water balances using commonly measured/modeled meteorological variables and information about the surface cover. It utilizes an evaporation-interception approach (Grimmond et al. 1991), similar to that used in forests, to model evaporation from urban surfaces.
     - The model uses seven surface types: paved, buildings, evergreen trees/shrubs, deciduous trees/shrubs, grass, bare soil and water. The surface state for each surface type at each time step is calculated from the running water balance of the canopy where the evaporation is calculated from the Penman-Monteith equation. The soil moisture below each surface type (excluding water) is taken into account.
     - Model applicability: Local scale – so forcing data should be above the height of the roughness elements (trees, buildings)

* Related Preprocessors
      `MetPreprocessor`, `ERA5`, `LandCoverReclassifier`, `LandCoverFraction(Point)`, `LandCoverFraction(Grid)`, `MorphometricCalculator(Point)`, `MorphometricCalculator(Grid)`, `SourceArea(Point)`, `SUEWSDatabase`, , `SUEWSDatabasePrepare`

* Dialog box
      .. figure:: /images/SUEWS_Advanced.jpg
          :width: 100%
          :align: center

          The dialog for SUEWS Advanced. Click on image for enlargement.

* Dialog sections
     -  When you run the plugin, you will see the dialog shown above. To use this plugin, all input data needs to be prepared beforehand. This can be done using the various plugins in the pre-processor in UMEP (see `ToolApplications`). The settings available in this plugin is used for specifying the settings for a specific model run. You should consult the manual (`<https://suews.readthedocs.io/en/latest/>`__) for instructions and information on what settings to use. 
     
     -  For extensive models run it is recommended to execute the model outside of QGIS (see `manual <https://suews.readthedocs.io/en/latest/>`__). 
     
     -  The interface above creates a so-called namelist (**RunControl.nml**) that is used be the model for general settings. After running the model, this file can be found in the suewsmodel directory in the UMEP plugin directory as well as in the input folder specified.
     
     -  It is always recommended to make use of a spin-up period to adjust e.g. water availbility in the model. This can be done by e.g. start your model before (months-years) the time period of interest.
     
     -  If you encounter memory issues calculating many grids and/or long time periods, you can divide the calculation in chunks as seen in the figure above.

* References:
      -  A full list of references related to the SUEWS model can be found at SUEWS manual (`<https://suews.readthedocs.io/en/latest/>`__).

