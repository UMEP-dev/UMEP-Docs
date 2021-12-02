.. _UWGReclassifier:

Urban Heat Island: UWG Reclassifier
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


.. note:: **UNDER CONSTRUCTION**


* Contributor:
    .. list-table::
       :widths: 50 50
       :header-rows: 1

       * - Name
         - Institution
       * - Fredrik Lindberg
         - Gothenburg
       * - Oskar Bäcklin
         - Gothenburg

* Introduction:
    The `Urban Weather Generator <UWG>` (UWG) tool is an implementation of the `Ladybug <https://github.com/ladybug-tools/uwg>`__ application with the same name. The `original Urban Weather Generator <http://urbanmicroclimate.scripts.mit.edu/uwg.php>`__ was developed by Bruno Bueno for `his PhD thesis at MIT <https://dspace.mit.edu/handle/1721.1/59107>`__. 
    
    The pre-processor UWG Reclassifier can be used to reclassify any vector polygon data of urban typologies (e.g. residential, commercial etc.) into urban weather generator (UWG) building classes. This is later used in the UWG Prepare plugin where input data for UWG is generated. UWG building templates is developed by `Aiko Nakano <https://dspace.mit.edu/handle/1721.1/108779>`__ and `Joseph Yang <https://dspace.mit.edu/handle/1721.1/107347>`__. Polygons of urban typologies should consider the neighborhood scale or larger.

* Dialog box:
    .. figure:: /images/UWGReclassifierInterface.jpg
        :align: center

        Dialog for the UWG Reclassifier plugin


* Parameters:

   .. list-table::
      :widths: 25 75
      :header-rows: 0
      
      * - Vector polygon grid
        - Vector polygon data that holds spatial information on urban typologies (e.g. residential, commercial etc.).
      * - Attribute field including urban topologies
        - Choose an attribute from the selected polygon layer where infomation on the urban topologies are stored.
      * - Attribute values
        - User defined urban typologies
      * - UWG building type
        - What building class that best represents the user defined urban typology
      * - Construction period
        - Time of construction (*pre80 = before 1980, pst80 = after 1980, New = recent*)

* Save as:
    The name and path to the shape file that will be created 

* Run:
    Starts the reclassification.

* Help
    Link to this manual page.

* Close:
    Closes the plugin.

* Remarks
      - There are possibilities to create new building types for the UWG. This, however, is not included here.
      - Polygons of urban typologies should consider the neighborhood scale or larger.
      - A tutorial is being constructed on how to analyse the urban heat island using UMEP.
