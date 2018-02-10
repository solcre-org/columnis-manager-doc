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