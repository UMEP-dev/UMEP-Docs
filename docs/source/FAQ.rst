.. _FAQ:



FAQ (Frequently Asked Questions)
--------------------------------
* How do I upgrade the plugin?
    When a new LTR version is released it will be available from the repository. In QGIS to check for updates, go to *Plugins>Manage and Install Plugins...*. If the UMEP plugin is in bold, a new version is available. On how to upgrade to the development version, see `Getting started <Getting_Started>`.

* How do I uninstall the plugin?
    Go to *Plugins>Manage and Install Plugins...*. Locate the UMEP plugin and click *Uninstall*.

* The Spatial Data Downloader is deprecated (as from July 2020). How can I obtain population density data from SEDAC?
    Visit our `YouTube Channel <https://www.youtube.com/channel/UCTPkXncD3ghb5ZTdZe_u7gA>`__ and watch the link on how to access Web Services using QGIS.

* How do I install other python packages (e.g. pandas) as well as other libraries not included in the Desktop Express Install of QGIS?
    Follow the instruction from this `link <Python_Libraries>`.

*  My new raster is just black after using e.g. the *Wall Height and Aspect* plugin. What is wrong?
    Probably nothing. Is is just QGIS that scales the a loaded raster by excluding outliers and if you have large areas with e.g. zeros (which you have in the resulting raster from this plugin) it looks like there is only zeros in your new raster. Go to properties of your new raster layers and reclassify your values that should be visualized.

* Can the UMEP-plugin be used when **Nodata**-values are present in the input rasters?
    Yes, it can but we strongly recommend you to reclassify Nodata values to e.g. 0 before using them in UMEP. Here is a forum discussion that can help: https://gis.stackexchange.com/questions/12418/redefining-nodata-value-into-zero-in-qgis

* Why is UMEP having problems saving output files?
    Check that your path contains only English characters. For Mac users: the UMEP graphical interface will occasionally want to create a folder instead of selecting a folder. In this case in *Save As:* write the folder name you would like to save your output, press *Save*, when it asks *“...folder name...” already exists. Do you want to replace it?* press *Replace*.

* How is frontal area index calculated in *Image Morphometric Parameters* plugins?
    Our method is only using one line through the center of the grid for each wind direction. This is because we rotate the DSM and hence it is only the center line that includes height information. We do this since we are using a pure raster-based approach and if we were to instead rotate the search direction vector we would end up with different lengths for each wind direction. If you want to investigate a certain wind direction I suggest that you use a section of wind directions; e.g. 45 degrees.

* How do I report a bug?
    Report it at the `repository <https://github.com/UMEP-dev/UMEP/issues>`__

* How do I report an issue with the manual?
    Report it at the `manual repository <https://github.com/UMEP-dev/UMEP-Docs/issues>`__

*  What can UMEP do?
    `Tool Architecture <PluginArchitecture>` provides an overview

*  Who has developed this?
    `People <People_Involved_&_Acknowledgements>` involved in development

*  What are the development guidelines?
    Information on development guidelines can be found `here <DevelopmentGuidelines>`.

* How can I uninstall QGIS?
    Uninstalling QGIS on a Windows PC is not done via the Control Panel as most other software. To uninstall completely, start the OSGeo4W setup (found in your start menu) and choose *Advanced install*. Continue until you come up to the window where you can add, remove and upgrade the different packages in your QGIS installation. Click on the small wheel with two arrows next to *Desktop* until *Uninstall* is seen. This removes shortcuts and most of the files related to QGIS. However, not all OSGeo products are removed. IF you want remove everything, open your File Explorer and remove the folder manually where you installed the OSGEO products (usually under *C:\\OSGeo4W64*).

          .. figure:: /images/Uninstall.png

              QGIS installation dialog (Advanced)

* How do I ask other questions?
   You can ask them at the `UMEP Community <https://github.com/UMEP-dev/UMEP/discussions>`_.
