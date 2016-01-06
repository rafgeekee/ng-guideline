## Controllers
  - Please note that controllers should not be used extensively, they are not necessarily a medium of creating logic but an exposure layer between the view and the model.

  - A controller is should only be used with a single directive, and a directive must not be associated with more that one controller.

### Example
###### [Style [S-C001](./#s-C001)]

  ```javascript
    'use strict';

    angular
      .module('product')
      .controller('productController', productController);

    productController.$inject = [
      '$scope',
      'productFactory',
      'productFilter',
      'flashMessage',
    ];

    /**
     * @class Product.Controller
     * @desc A description
     * @memberOf Product
     */
    function productController($scope, productFactory, productFilter, flashMessage) {
      let vmProduct = this;

      vmProduct.data = null;
      vmProduct.getFilteredProduct = getFilteredProduct;
      getData();

      ///////////

      /**
       * @function getData
       * @desc Initialization method for the controller.
       * @returns {Promise}
       * @memberOf Product.Controller
       */
      function getData() {
        return productFactory.getData()
          .then((data) => {
            return vmProduct.data = data;
          })
          .catch((error) => {
            flashMessage.error(flashMessage);
          });
      }

      /**
       * @function getFilteredProduct
       * @desc Filters the product data
       * @returns {Promise}
       * @memberOf Product.Controller
       */
      function getFilteredProduct() {
        return productFilter(vmProduct.data);
      }
    }
  ```

### Documentation
###### [See \[Style S-OD001\]](./organisation-documentation.md#s-od001)

### Organisation
###### [See \[Style S-OD002\]](./organisation-documentation.md#s-od002)

### Exposure and hidden implementation
###### [See \[Style S-OD003\]](./organisation-documentation.md#s-od003)

### Assignment
###### [See \[Style S-DA001\]](./di-assignment.md#s-da001)

### Dependency Injection
###### [See \[Style S-DA002\]](./di-assignment.md#s-da002)

### const or let
###### [See \[Style S-JS001\]](./js-guidelines.md#s-js001)

### ES6 Arrow functions
###### [See \[Style S-JS002\]](./js-guidelines.md#s-js002)

### ControllerAs with vm[CamelCaseName]
###### [Style [Y031](https://github.com/johnpapa/angular-styleguide/#style-y031)]

  - *See [directives with controllerAs](https://github.com/johnpapa/angular-styleguide/#style-y075)* for integration of controller (controllerAs) with directives.

  - Use the `controllerAs` syntax over the `classic controller with $scope` syntax.

  - The `controllerAs` syntax uses `this` inside controllers which gets bound to `$scope`

  - It provides a isolated object to the scope. So when you have a controllerAs set to `vmProduct`, that object is placed on your isolated scope as `$scope.vmProduct`. This prevents any cross contamination between directives as they are all completely isolated from each other.

  - Your controllers act as a gateway, they prevent cross contamination to help modulise code, and expose what is needed to the $scope. You may find that you write a little more integration for exposure, but as you write more logic to services you will find the simplicity of the codebase improve dramatically.

  *Why?*: `controllerAs` is syntactic sugar over `$scope`. You can still bind to the View and still access `$scope` methods.

  *Why?*: Helps avoid the temptation of using `$scope` methods inside a controller when it may otherwise be better to avoid them or move the method to a factory, and reference them from the controller. Consider using `$scope` in a controller only when needed. For example when publishing and subscribing events using [`$emit`](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$emit), [`$broadcast`](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$broadcast), or [`$on`](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$on).


### Controller focus with logic to Services
###### [Style [Y035](https://github.com/johnpapa/angular-styleguide/#style-y035)]

  - Defer logic in a controller by delegating to services and factories.

    *Why?*: Logic may be reused by multiple controllers when placed within a service and exposed via a function.

    *Why?*: Logic in a service can more easily be isolated in a unit test, while the calling logic in the controller can be easily mocked.

    *Why?*: Removes dependencies and hides implementation details from the controller.

    *Why?*: Keeps the controller slim, trim, and focused.

  - Define a controller for a view, and try not to reuse the controller for other views. Instead, move reusable logic to factories and keep the controller simple and focused on its view.

    *Why?*: Reusing controllers with several views is brittle and good end-to-end (e2e) test coverage is required to ensure stability across large applications.

### Assigning Route based Controllers
###### [Style [Y038](https://github.com/johnpapa/angular-styleguide/#style-y038)]

  - When a controller must be paired with a view and either component may be re-used by other controllers or views, define controllers along with their routes.

    *Why?*: Pairing the controller in the route allows different routes to invoke different pairs of controllers and views. When controllers are assigned in the view using [`ng-controller`](https://docs.angularjs.org/api/ng/directive/ngController), that view is always associated with the same controller.

**[Back to table of contents](../README.md/#table-of-contents)**
