Project Structure
=================

The Columnis Manager code is located inside the ``src/app`` folder, where we will find 3 main folders, ``configs``, ``panels`` and ``shared``.

- ``src/``
    - ``app/``
        - ``configs/``: general configurations
        - ``panels/``: panels are located
        - ``shared/``: components shared between all the panels
            - ``controllers/``: core controllers
            - ``directives/``: core directives
            - ``filters/``: core filters
            - ``interceptors/``: core http interceptors
            - ``partials/``: directives and generic html partials
            - ``services/``: core and helper services
    - ``images/``: image and icons assets
    - ``scripts/``: bower dependencies
    - ``scss/``: sass styles generated into css folder

Configurations
--------------
Columnis Manager configurations is located inside de folder ``src/app/configs``, all the configurations has the ``.json`` extension, in runtime each file generates a ``.js`` files and the project uses this JavaScripts files.

.. note::

    If you make changes to ``.json`` files, you must run again the project to see the changes.

- ``config.json``: general configurations
- ``requirejs.conf.json``: requires configuration with all dependencies of third-party libraries
- ``translate.json``: general translations
- ``dependencies.json``: all core ``.js`` files
- ``async.dependencies.json``: third-party libraries who can loads from any ``state.json``.

Panels
------
All the panels files are placed here in the folder ``src/app/panels``, the panel must have this structure:

- ``[PANEL_NAME]``
    - controllers/``[PANEL_NAME]Controller.js``
    - services/``[PANEL_NAME]Service.js`` `(optional)`
    - partials/index.html
    - config.js
    - menu.json `(only for root states)`
    - state.json
    - translate.js

config.js
~~~~~~~~~
The panel configuration must be here, the file is a plain js file and must define the panel configuration, It starts with ``Configuration.[PANEL_NAME]``.

* ``config``: panel configuration
    * ``name``: string used for identify panel and it is used for set the placeholder image like ``<IMAGE_DIR>/panel-icons/[name].svg``
    * ``placeholder``: sets the placeholder text
    * ``description``: sets the placeholder title attribute value
    * ``messages_prefix``: string used to identify loaders
    * ``messages_list_prefix``: string used to identify list loaders `(Composite panels)`
    * ``endpoint``: resource uri without domain, it must be with $resource conventions
    * ``endpointList``: resource uri without domain used in list, it must be with $resource conventions `(Composite panels)`
    * ``parent_field``: field name used to fetch items to table or grid, filtered by the list item `(Composite panels)`
    * ``file_upload``: enable the form data to the primary resource, it is used when the resource need file upload 
    * ``file_list_upload``: enable the form data to the list resource, it is used when the resource need file upload `(Composite panels)`
    * ``with_thumb``: enable table thumbs
    * ``sortable_table``: enable the sorting functionality to the table or grid
    * ``save_all_fields``: sets the fields that are sends in the request after saves sorting order
    * ``sortable_field``: the object key where the sorting value are saved
    * ``addTitles``: configure the modal title when adding, is a json object where the key is the modal id and the value is the title
    * ``tabs``: configure and enables modal tabs, is a json where the key is the modal id and the value is an array with each tab title
    * ``keep_list``: prevent reset list when initializes the panel `(Composite panels)`
    * ``blockInit``: prevent panel initial fetch
    * ``blockListInit``: prevent panel list initial fetch `(Composite panels)`
    * ``deleteFields``: sets the fields that are sends in the request when deleting multiple items
    * ``dynamicTable``: enable dynamic table mode, it load table columns and table headers dynamically from the object.data keys
    * ``without_footer``: disable footer padding
    * ``layout``: sets the layout, it can be ``grid``, ``list`` or ``table``
    * ``massive_fields``: sets the massive fields configuration, is a array of jsons with id and display keys, where id key is the field name and display are the label text 
    * ``disableAdd``: disable add button from placeholder and modal header
    * ``disableSave``: disable save button form modal header
    * ``disableModify``: disable modify button from modal header in detail mode
    * ``customHeaderButton``: enable custom button in the modal header
    * ``customHeaderButtonText``: sets the custom header button text in the modal header
* ``forms``: forms validations
    * TODO
* ``list``: list structure and configuration `(only composite panels)`
    * TODO
* ``table``: table structure and configuration
    * TODO

Example config.js file (from a panel with composite directive):

.. code-block:: js

    Configuration.example = {
        "config": {
            "name": "panel-example",
            "placeholder": "EXAMPLE_PLACEHOLDER_TRANSLATED",
            "description": "Example text",
            "messages_prefix": "example",
            "messages_list_prefix": "list-example",
            "endpoint": "/examples/:id", 
            "endpointList": "/examples/:exampleId/:id",
            "parent_field": "exampleId",
            "file_upload": false,
            "file_list_upload": false,
            "with_thumb": false,
            "sortable_table": false,
            "save_all_fields": [ 'id', 'order' ],
            "sortable_field": "order",
            "addTitles": { 0: "EXAMPLE_ADD_TITLE" },
            "tabs": { 0: [ 'TAB_1', 'TAB_2' ] },
            "keep_list": false,
            "blockInit": false,
            "blockListInit": false,
            "deleteFields": [ 'id' ],
            "dynamicTable": false,
            "without_footer": false,
            "layout": "table",
            "massive_fields": [ { "id": "exampleKey", "display": "EXAMPLE_KEY_LABEL" } ],
            "disableAdd": false,
            "disableSave": false,
            "disableModify": false,
            "customHeaderButton": false,
            "customHeaderButtonText": ""
        },
        "forms": {},
        "list": {},
        "table": {}
    }