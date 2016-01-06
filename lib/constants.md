## Constants

### Vendor Globals
###### [Style [Y240](https://github.com/johnpapa/angular-styleguide/#style-y240)]

  - Create an Angular Constant for vendor libraries' global variables.

    *Why?*: Provides a way to inject vendor libraries that otherwise are globals. This improves code testability by allowing you to more easily know what the dependencies of your components are (avoids leaky abstractions). It also allows you to mock these dependencies, where it makes sense.

    ```javascript
      'use strict';

      /**
       * @namespace App.Core
       * @desc A description
       * @memberOf App
       */
      angular
        .module('app.core')
        .constant('toastr', toastr)
        .constant('moment', moment);
    ```

###### [Style [Y241](https://github.com/johnpapa/angular-styleguide/#style-y241)]

  - Use constants for values that do not change and do not come from another service. When constants are used only for a module that may be reused in multiple applications, place constants in a file per module named after the module. Until this is required, keep constants in the main module in a `constants.js` file.

    *Why?*: A value that may change, even infrequently, should be retrieved from a service so you do not have to change the source code. For example, a url for a data service could be placed in a constants but a better place would be to load it from a web service.

    *Why?*: Constants can be injected into any angular component, including providers.

    *Why?*: When an application is separated into modules that may be reused in other applications, each stand-alone module should be able to operate on its own including any dependent constants.

    ```javascript
    // Constants used by the entire app
    angular
      .module('app.core')
      .constant('moment', moment);

    // Constants used only by the sales module
    angular
        .module('app.product')
        .constant('events', {
            PRODUCT_UPDATED: 'event_product_updated',
        });
    ```

**[Back to table of contents](../README.md/#table-of-contents)**
