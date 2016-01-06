## Startup Logic

### Configuration
###### [Style [Y170](https://github.com/johnpapa/angular-styleguide/#style-y170)]

  - Inject code into [module configuration](https://docs.angularjs.org/guide/module#module-loading-dependencies) that must be configured before running the angular app. Ideal candidates include providers and constants.

    *Why?*: This makes it easier to have less places for configuration.

  ```javascript
    'use strict';

    angular
      .module('app')
      .config(configuration);

    configuration.$inject = [
      'toastr',
    ];

    /**
     * @class App.Configuration
     * @desc A description
     * @memberOf App
     */
    function configuration(toastr) {
      toastr.options.timeOut = 4000;
      toastr.options.positionClass = 'toast-bottom-right';

      ////////////////

      // Space is reserved for methods
    }  
  ```

### Run Blocks
###### [Style [Y171](https://github.com/johnpapa/angular-styleguide/#style-y171)]

  - Any code that needs to run when an application starts should be declared in a factory, exposed via a function, and injected into the [run block](https://docs.angularjs.org/guide/module#module-loading-dependencies).

    *Why?*: Code directly in a run block can be difficult to test. Placing in a factory makes it easier to abstract and mock.

  ```javascript
    'use strict';

    angular
      .module('app')
      .run(runBlock);

    runBlock.$inject = [
      'authenticator',
      'translator',
    ];

    /**
     * @class App.RunBlock
     * @desc A description
     * @memberOf App
     */
    function runBlock(authenticator, translator) {
      authenticator.initialize();
      translator.initialize();
    }
  ```

**[Back to table of contents](../README.md/#table-of-contents)**
