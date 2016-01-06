## Naming

### Naming Guidelines
###### [Style [Y120](https://github.com/johnpapa/angular-styleguide/#style-y120)]

  - Use consistent names for all components following a pattern that describes the component's feature then (optionally) its type. My recommended pattern is `featureType.js`. There are 2 names for most assets:
    * the file name (`avengersController.js`)
    * the registered component name with Angular (`AvengersController`)

    *Why?*: Naming conventions help provide a consistent way to find content at a glance. Consistency within the project is vital. Consistency with a team is important.

    *Why?*: The naming conventions should simply help you find your code faster and make it easier to understand.

### Feature File Names
###### [Style [Y121](https://github.com/johnpapa/angular-styleguide/#style-y121)]

  - Use consistent names for all components following a pattern that describes the component's feature then (optionally) its type. My recommended pattern is `featureType.js`.

    *Why?*: Provides a consistent way to quickly identify components.

    *Why?*: Provides pattern matching for any automated tasks.

    ```javascript

    // File names

    // Module
    productModule.js

    // Directives
    productDirective.js

    // Controllers
    productController.js

    // Services/Factories
    productService.js
    productFactory.js

    // routes
    productRoutes.js

    // templates (no suffix as we know its a template)
    product.html

    ```

    ```javascript

    // Angular naming

    // Module
    angular.module('product', []);

    // Directives (xx[CamelCaseName])
    angular.module('product')
      .directive('seProduct');

    // Controllers
    angular.module('product')
      .controller('productController');

    // Services/Factories
    angular.module('product')
      .factory('productService');

    // Service/Factory with a clear identifiable name
    angular.module('app.core')
      .factory('logger');

    ```

### Test File Names
###### [Style [Y122](https://github.com/johnpapa/angular-styleguide/#style-y122)]

  - Name test specifications similar to the component they test with a suffix of `-spec`.

    *Why?*: Provides a consistent way to quickly identify components.

    *Why?*: Provides pattern matching for [karma](http://karma-runner.github.io/) or other test runners.

**[Back to table of contents](../README.md/#table-of-contents)**
