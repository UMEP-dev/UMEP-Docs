.. _TreePlanter:

Outdoor Thermal Comfort: TreePlanter
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note:: Under Construction. NOT READY.

* Contributors:
   .. list-table::
      :widths: 50 50
      :header-rows: 1

      * - Name
        - Institution
      * - Nils Wallenberg
        - Gothenburg
      * - Fredrik Lindberg
        - Gothenburg

* Introduction
    -  The **TreePlanter** plugin is a model for optimization of tree arrangement to mitigate thermal heat stress with respect to radiant load represented by mean radiant temperature (T\ :sub:`mrt`). The optimization of tree arrangement is achieved by utilizing a metaheuristic hill-climbing algorithm that evaluates the combined shading effect of 1 to N trees and their corresponding mitigating decrease in T\ :sub:`mrt`.
    -  The TreePlanter is only available via `UMEPforProcessing`.

* Related Preprocessors and Processors
   `MetPreprocessor`, `ERA5`, `SkyViewFactorCalculator`, `WallHeightandAspect`, `SOLWEIG`

* Dialog box
   .. figure:: /images/TreePlanterInterface.jpg
      :width: 100%
      :align: center

      The dialog for the TreePlanter model. Click on image for enlargement.

* Input Parameters 
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Path to SOLWEIG output directory
        - text
      * - Planting area (Vector polygon)
        - text
      * - From (hour)
        - text
      * - Thru (hour)
        - text
      * - Tree type
        - text
      * - osv
        - osv

* Advanced Parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Number of restart iterations
        - text
      * - osv
        - osv

* Output parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Canopy Digital Surface Model
        - text
      * - osv
        - osv


* Run
    Starts the calculations. As TreePlanter is computationally expensive model, large grids (i.e. high number of pixels), high number of trees and/or many time steps will take a relatively long time to compute. Since TreePlanter is incorporated in the Processing Toolbox in QGIS, the software can still be used while locations of trees is calculated.

* Help
    Link to this manual.

* Close
    Closes the plugin.

* Quick example on how to run TreePlanter
             #. Download the (`test dataset <https://urban-meteorology-reading.github.io>`__).
             #. Add the raster layers (DSM, CDSM and land cover) from the Goteborg folder into a new QGIS session. The coordinate system of the grids is **Sweref99 1200 (EPSG:3007)**.
             #. In order to run SOLWEIG, some additional datasets must be created based on the raster grids you just added. Open the SkyViewFactor Calculator from the UMEP Pre-processor and calculate SVFs using both your DSM and CDSM. Leave all other settings as default.
             #. Open the Wall height and aspect plugin from the UMEP Pre-processor and calculate both wall height and aspect using the DSM and your input raster. Tick in the box to add them to your project. Leave all other settings as default.
             #. Now you are ready to generate your first T\ :sub:`mrt` map. Open SOLWEIG and use the settings as shown in the figure below but replace the paths to the fit your computer environment. When you are finished, press *Run*.

 
* Remarks
      -  All DSMs need to have the same extent and pixel size.
      -  This plugin is computationally intensive i.e. large grids will take a lot of time and very large grids will not be possible to use. Large grids e.g. larger than 4000000 pixels should preferably be tiled before.
      -  SOLWEIG focus on pedestrian radiation fluxes and it is not recommended to consider fluxes on building roofs.

* References
      -  Wallenberg and Lindberg...
