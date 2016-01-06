## Services (Factories)

  - Services are instantiated with the `new` keyword, use `this` for public methods and variables. Since these are so similar to factories, use a factory instead for consistency.

    Note: [All Angular services are singletons](https://docs.angularjs.org/guide/services). This means that there is only one instance of a given service per injector.


  - Refactor logic for making data operations and interacting with data to a factory. Make data services responsible for XHR calls, local storage, stashing in memory, or any other data operations.

    *Why?*: The controller's responsibility is for the presentation and gathering of information for the view. It should not care how it gets the data, just that it knows who to ask for it. Separating the data services moves the logic on how to get it to the data service, and lets the controller be simpler and more focused on the view.

    *Why?*: This makes it easier to test (mock or real) the data calls when testing a controller that uses a data service.

    *Why?*: Data service implementation may have very specific code to handle the data repository. This may include headers, how to talk to the data, or other services such as `$http`. Separating the logic into a data service encapsulates this logic in a single place hiding the implementation from the outside consumers (perhaps a controller), also making it easier to change the implementation.

    Note: The data service is called from consumers, such as a controller, hiding the implementation from the consumers, as shown below.

  - When calling a data service that returns a promise such as `$http`, return a promise in your calling function too.

    *Why?*: You can chain the promises together and take further action after the data call completes and resolves or rejects the promise.

### Example
###### [Style [S-S001](./#s-s001)]

  ```javascript
    'use strict';

    angular
      .module('product')
      .factory('productFactory', productFactory);

    productFactory.$inject = [
    	'productRestFactory',
    	'logger',
    ];

    /**
     * @class Product.Factory
     * @desc A description
     * @memberOf Product
     */
    function productFactory(productRestFactory, logger) {
      let service = {
        getData
      };
      return service;

      ///////////

      /**
       * @function getData
       * @desc Gets data about the product
       * @returns {Promise}
       * @memberOf Product.Factory
       */
      function getData() {
        return productRestFactory.getData()
          .then((response) => {
            return response.data.results;
          })
          .catch((error) => {
            logger.error('Unable to get data.' + error.data);
          });
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

  ```javascript
    /**
     * @class Product.Factory
     * @desc A description
     * @memberOf Product
     */
    function productFactory(productRestFactory, logger) {
      let service = {
        getData
      };
      return service;

      ///////////

      /**
       * @function getData
       * @desc Gets data about the product
       * @returns {Promise}
       * @memberOf Product.Factory
       */
      function getData() {
        // gets data
      }
    }
  ```

### const or let
###### [See \[Style S-JS001\]](./js-guidelines.md#s-js001)

### Service exception and resolve handling
###### [Style [S-S002](./#s-s002)]
  - Services may handle exception handling to a certain degree. There level of exception handling should be to a level where it handles any updates to data held in the service, and any development logging. Exception handling should not do anything such as displaying a flash message or popup as depending on the use case either could be valid. This should be done in the relevant controller.

  - The resolving of a request should be used to update any data held in the service, and manipulate the returned data into a better format. Resolve handling should not do any additional logic like applying a digest.

    ```javascript
      function getData() {
        return productRestFactory.getData()
          .then((response) => {
            return response.data.results;
          })
          .catch((error) => {
            logger.error('Unable to get data.' + error.message);
          });
      }
    ```

### ES6 Arrow functions
###### [See \[Style S-JS002\]](./js-guidelines.md#s-js002)

**[Back to table of contents](../README.md/#table-of-contents)**
