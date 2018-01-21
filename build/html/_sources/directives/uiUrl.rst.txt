UiUrlDirective
=================
``Element`` directive for model values like urls.

Files
~~~~~
..  code-block:: html

        src/shared/directives/UiUrlDirective.js
        src/shared/partials/ui-url.html

Options
~~~~~~~
Directive options from ``scope`` vars:

======================  ==================  ===============================
         Option                Type                     Comments
======================  ==================  ===============================
 ``obj``                 Two way bindings    Model reference
 ``label``               Text                Text with label text
 ``fieldPlaceholder``    Text                Text with placeholder text
 ``onKeyDown``           Two way bindings    Model with key down callback
======================  ==================  ===============================

Example
~~~~~~~
.. code-block:: html

        <ui-url
            obj="myUrlModel"
            label="My url:"
            field-placeholder="Enter the url"
            on-change="onMyUrlChange">
        </ui-url>