## Modules

### Example
###### [Style [SM001](./#s-m001)]
  - This is an example `productModule.js` file. We will go through each part in more detail.

    ```javascript
      /**
       * Product Module
       * @namespace Product
       */
      'use strict';

      /**
       * @class Product.Module
       * @memberOf Product
       * @desc A description
       */
      angular
        .module('product', [
          'dependency1',
          'dependency2',
        ]);
    ```

### Documentation
###### [See \[Style S-OD001\]](./organisation-documentation.md#s-od001)

### Organisation
###### [See \[Style S-OD002\]](./organisation-documentation.md#s-od002)

### Assignment
###### [See \[Style S-DA001\]](./di-assignment.md#s-da001)

  - Setting a module
    ```javascript

    angular
      .module('product', [
        'dependency1',
        'dependency2',
      ]);

    ```

  - A module should only be created once, then retrieved from that point.

    ```javascript

      angular
        .module('product');

    ```

  - Use unique naming conventions with separators for sub-modules.

    *Why?*: Unique names help avoid module name collisions. Separators help define modules and their submodule hierarchy. For example `app` may be your root module while `app.dashboard` and `app.users` may be modules that are used as dependencies of `app`.

### Dependency Injection
###### [See \[Style S-DA002\]](./di-assignment.md#s-da002)

**[Back to table of contents](../README.md/#table-of-contents)**
