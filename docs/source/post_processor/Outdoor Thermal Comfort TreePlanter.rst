.. _TreePlanter:

Outdoor Thermal Comfort: TreePlanter
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
    -  The **TreePlanter** plugin is a model for optimization of tree arrangement to mitigate thermal heat stress with respect to radiant load represented by mean radiant temperature (T\ :sub:`mrt`). The optimization of tree arrangement is achieved by utilizing a metaheuristic hill climbing algorithm that evaluates the combined shading effect of 1 to N trees and their corresponding mitigating decrease in T\ :sub:`mrt`.
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
        - Path that contains necessary files from SOLWEIG run.
      * - Planting area (Vector polygon)
        - A vectory polygon that depicts the planting area.
      * - From (hour)
        - Starting hour of analysis.
      * - Thru (hour)
        - Ending hour of analysis.
      * - Tree type
        - Decideuous or coniferuous tree.
      * - Tree height (meter above ground level)
        - Tree height from ground to top of canopy (in meters).
      * - Tree canopy diameter (meter)
      	- Tree canopy diameter (in meters).
      * - Trunk zone height (meter above ground level)
      	- Height of bare trunk between ground and canopy.
      * - Transmissivity of light through vegetation (%)
      	- Sets how much of the solar irradiance that will penetrate though the canopy (0-100 %), where 0 is none and 100 is all irradiance.
      * - Number of trees to plant
      	- Number of trees for which the model will search for optimized positions.

* Advanced Parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Number of restart iterations
        - Number of times the model will restart with new starting positions for the trees.
      * - Allow areas outside Planting area to be included in calculation
        - If ticked, areas outside Planting area are included in the TreePlanter calculations and can be shaded by the trees.
      * - Use random starting positions in the hill climbing algorithm
      	- If ticked, the trees will start with random starting positions in each iteration. If not ticked, the starting positions will be based on the local optimal positions of the previous iteration.
      * - Use a greedy algorithm to position trees
      	- Disables the hill climbing algorithm and enables the greedy algorithm. The greedy algorithm finds positions for trees one at a time. This enables positioning of large number of trees in large areas.

* Output parameters
   .. list-table::
      :widths: 25 75
      :header-rows: 0

      * - Canopy Digital Surface Model
        - Output is a Canopy Digital Surface Model (CDSM) with the positions of the new trees. If a CDSM with existing trees were included as input data to the SOLWEIG run, it will be updated to include the new trees.
      * - Vector point file with tree location(s)
        - Output is a vector point file with the positions of the new trees.


* Run
    Starts the calculations. As TreePlanter is computationally expensive model, large grids (i.e. high number of pixels), high number of trees and/or many time steps will take a relatively long time to compute. Since TreePlanter is incorporated in the Processing Toolbox in QGIS, the software can still be used while locations of trees is calculated.

* Help
    Link to this manual.

* Close
    Closes the plugin.

* Quick example on how to run TreePlanter
             #. Download the `TreePlanter test dataset <https://github.com/Urban-Meteorology-Reading/Urban-Meteorology-Reading.github.io/blob/master/other%20files/TreePlanterTestData.zip>`__.
             #. Add the raster layers (DEM, DSM and CDSM) from the Goteborg folder into a new QGIS session. The coordinate system of the grids is **Sweref99 1200 (EPSG:3007)**.
             #. Run SOLWEIG (see `Introduction to SOLWEIG <https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/IntroductionToSolweig.html>`__). Remember to tick **Save necessary raster(s) for the TreePlanter tool**.
             #. Now you are ready to generate positions for trees. Open TreePlanter and use the settings as shown in the figure below but replace the Path to SOLWEIG output directory and paths to output files to the fit your computer environment. When you are finished, press *Run*.

   .. figure:: /images/TreePlanterQuickRun.jpg
      :width: 100%
      :align: center

      Settings for a first try with the TreePlanter model. Click on image for enlargement.
 
* Remarks
      -  This plugin is computationally intensive i.e. large grids will take a lot of time and very large grids will not be possible to use. If on a large grid, consider using a small number of trees or the greedy algorithm.
      -  The greedy algorithm should be used when running the model with large number of trees.

* References
      -  Wallenberg, N., Lindberg, F., and Rayner, D.: Locating trees to mitigate outdoor radiant load of humans in urban areas using a metaheuristic hill-climbing algorithm – introducing TreePlanter v1.0, Geosci. Model Dev., 15, 1107–1128, https://doi.org/10.5194/gmd-15-1107-2022, 2022.
