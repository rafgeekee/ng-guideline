# Angular Guideline

## Purpose
The purpose of this is to set provide a rough guide for JavaScript and Angular syntax, conventions, and structuring. To support the building of the Angular Applications. The main ideology is to set a style of coding that provides a capable foundation to improve maintainability, readability and performant code.

## Credit and amendments
Never work in a vacuum. If you find any other resource or have any questions about any of this guide; please speak up - so we can improve the guidelines and maintain a robust codebase.

This guide is based on https://github.com/johnpapa/angular-styleguide, it has been reduced to the core aspects to the structure of the project and its files. For more information on parts of the guide please read the original guideline as its more comprehensive. The original guideline also provides information on further best practices for development with angular. Such as Automation and generators.

## Style codes
* *[Style [Y{number}](#style-y001)]*: are from the original [Angular Guidelines](https://github.com/johnpapa/angular-styleguide).
* *[Style [S{number}](#style-s001)]*: are Styles formatted by Sainsbury's, based on our time spent with angular.

## Notes
This guideline is not absolute. It should be used as a means of a tool and a guide to help build better applications, there may be instances where some Styles do not fit into the format of a project.

This guideline is still in development. It will be improved upon over time, as we learn and discover the force.

## Table of Contents
  1. [JavaScript Guidelines](#javascript-guidelines)
  1. [Use of plugins and libraries](#use-of-plugins-and-libraries)
  1. [Application Structure LIFT Principle](#application-structure-lift-principle)
  1. [Naming](#naming)
  1. [Modularity](#modularity)
  1. [Modules](#modules)
  1. [Factories](#factories-services)
  1. [Filters](#controllers)
  1. [Controllers](#controllers)
  1. [Directives](#directives)
  1. [One Time Binding](#one-time-binding)
  1. [Startup Logic](#startup-logic)
  1. [Angular $ Wrapper Services](#angular--wrapper-services)
  1. [Constants](#constants)
  1. [Routing](#routing)

## JavaScript Guidelines
To provide a better code base we will be using [Babel](https://babeljs.io/), this is a ES6 to ES5 compiler. It creates a better code base with stronger structure to code. It has some limitations to what can be converted to ES5 so please take care and fully study babel's guides to understand what can not be easily compiled.

To accompany this guide, it is highly recommended to fully read the [Airbnb JavaScript Guidelines](https://github.com/airbnb/javascript). It provides great insight into improving JavaScript code to make it more maintainable and readable.

## Use of plugins and libraries
When deciding to use and libraries or plugins please consider the use of them carefully, evaluate it's benefits and negatives and the overhead.

Before using a library please consult others to get there opinions and get it signed of by a team lead. It must also be highlighted that additional use of plugins and libraries should be minimized where possible, as it causes large overheads on page load. All JavaScript files get interpreted upon initialization of a page it can build up affecting load times significantly.

## Application Structure LIFT Principle
### LIFT
###### [Style [Y140](#style-y140)]

  - Structure your app such that you can `L`ocate your code quickly, `I`dentify the code at a glance, keep the `F`lattest structure you can, and `T`ry to stay DRY. The structure should follow these 4 basic guidelines.

    *Why LIFT?*: Provides a consistent structure that scales well, is modular, and makes it easier to increase developer efficiency by finding code quickly. Another way to check your app structure is to ask yourself: How quickly can you open and work in all of the related files for a feature?

    When I find my structure is not feeling comfortable, I go back and revisit these LIFT guidelines

    1. `L`ocating our code is easy
    2. `I`dentify code at a glance
    3. `F`lat structure as long as we can
    4. `T`ry to stay DRY (Don’t Repeat Yourself) or T-DRY

### Locate
###### [Style [Y141](#style-y141)]

  - Make locating your code intuitive, simple and fast.

    *Why?*: I find this to be super important for a project. If the team cannot find the files they need to work on quickly, they will not be able to work as efficiently as possible, and the structure needs to change. You may not know the file name or where its related files are, so putting them in the most intuitive locations and near each other saves a ton of time. A descriptive folder structure can help with this.

    ```
      /bower_components
      /src
        /app
          /components
            /basket
              basket.html
              basketController.js
              basketConstants.js
              basketDirective.js
              basketFactory.js
              basketModule.js
              basketRunBlock.js

            /hero
              hero.html
              heroController.js
              heroDirective.js
              heroModule.js
            /product
              /ebooks
                ebooksProduct.html
                ebooksProductController.js
                ebooksProductDirective.js
                ebooksProductFactory.js
                ebooksProductModule.js
              /music
                musicProduct.html
                musicProductController.js
                musicProductDirective.js
                musicProductFactory.js
                musicProductModule.js
              productFactory.js
              productModule.js
          /pages
            /landing
              /ebooks
                ebooksLandingPage.html
                ebooksLandingPageController.js
              /music
                musicLandingPage.html
                musicLandingPageController.js
            /product
              /ebooks
                ebooksProductPage.html
                ebooksProductPageController.js
              /music
                musicProductPage.html
                musicProductPageController.js
          /shared
            /filters
              someFilter.js
          appModule.js   
          appConstants.js   
          appRunBlock.js
        /toolkit
          /services
            basketRestFactory.js
            productRestFactory.js    
          toolkitModule.js   
          toolkitConstants.js   
          toolkitRunBlock.js
        index.html
    ```

### Identify
###### [Style [Y142](#style-y142)]

  - When you look at a file you should instantly know what it contains and represents.

    *Why?*: You spend less time hunting and pecking for code, and become more efficient. If this means you want longer file names, then so be it. Be descriptive with file names and keeping the contents of the file to exactly 1 component. Avoid files with multiple controllers, multiple services, or a mixture. There are deviations of the 1 per file rule when I have a set of very small features that are all related to each other, they are still easily identifiable.

### Flat
###### [Style [Y143](#style-y143)]

  - Keep a flat folder structure as long as possible. When you get to 7+ files, begin considering separation.

    *Why?*: Nobody wants to search 7 levels of folders to find a file. Think about menus on web sites … anything deeper than 2 should take serious consideration. In a folder structure there is no hard and fast number rule, but when a folder has 7-10 files, that may be time to create subfolders. Base it on your comfort level. Use a flatter structure until there is an obvious value (to help the rest of LIFT) in creating a new folder.

### T-DRY (Try to Stick to DRY)
###### [Style [Y144](#style-y144)]

  - Be DRY, but don't go nuts and sacrifice readability.

    *Why?*: Being DRY is important, but not crucial if it sacrifices the others in LIFT, which is why I call it T-DRY. I don’t want to type session-template.html for a template because, well, it’s obviously a template. If it is not obvious or by convention, then I name it.

**[Back to top](#table-of-contents)**

## Naming

### Naming Guidelines
###### [Style [Y120](#style-y120)]

  - Use consistent names for all components following a pattern that describes the component's feature then (optionally) its type. My recommended pattern is `featureType.js`. There are 2 names for most assets:
    * the file name (`avengersController.js`)
    * the registered component name with Angular (`AvengersController`)

    *Why?*: Naming conventions help provide a consistent way to find content at a glance. Consistency within the project is vital. Consistency with a team is important.

    *Why?*: The naming conventions should simply help you find your code faster and make it easier to understand.

### Feature File Names
###### [Style [Y121](#style-y121)]

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
###### [Style [Y122](#style-y122)]

  - Name test specifications similar to the component they test with a suffix of `-spec`.

    *Why?*: Provides a consistent way to quickly identify components.

    *Why?*: Provides pattern matching for [karma](http://karma-runner.github.io/) or other test runners.

**[Back to top](#table-of-contents)**

## Modularity

### Many Small, Self Contained Modules
###### [Style [Y160](#style-y160)]

  - Create small modules that encapsulate one responsibility.

    *Why?*: Modular applications make it easy to plug and go as they allow the development teams to build vertical slices of the applications and roll out incrementally. This means we can plug in new features as we develop them.

### Create an App Module
###### [Style [Y161](#style-y161)]

  - Create an application root module whose role is pull together all of the modules and features of your application. Name this for your application.

    *Why?*: Angular encourages modularity and separation patterns. Creating an application root module whose role is to tie your other modules together provides a very straightforward way to add or remove modules from your application.

### Keep the App Module Thin
###### [Style [Y162](#style-y162)]

  - Only put logic for pulling together the app in the application module. Leave features in their own modules.

    *Why?*: Adding additional roles to the application root to get remote data, display views, or other logic not related to pulling the app together muddies the app module and make both sets of features harder to reuse or turn off.

    *Why?*: The app module becomes a manifest that describes which modules help define the application.

### Feature Areas are Modules
###### [Style [Y163](#style-y163)]

  - Create modules that represent feature areas, such as layout, reusable and shared services, dashboards, and app specific features (e.g. customers, admin, sales).

    *Why?*: Self contained modules can be added to the application with little or no friction.

    *Why?*: Sprints or iterations can focus on feature areas and turn them on at the end of the sprint or iteration.

    *Why?*: Separating feature areas into modules makes it easier to test the modules in isolation and reuse code.

### Reusable Blocks are Modules
###### [Style [Y164](#style-y164)]

  - Create modules that represent reusable application blocks for common services such as exception handling, logging, diagnostics, security, and local data stashing.

    *Why?*: These types of features are needed in many applications, so by keeping them separated in their own modules they can be application generic and be reused across applications.

### Module Dependencies
###### [Style [Y165](#style-y165)]

  - The application root module depends on the app specific feature modules and any shared or reusable modules.

    ![Modularity and Dependencies](https://raw.githubusercontent.com/johnpapa/angular-styleguide/master/assets/modularity-1.png)

    *Why?*: The main app module contains a quickly identifiable manifest of the application's features.

    *Why?*: Each feature area contains a manifest of what it depends on, so it can be pulled in as a dependency in other applications and still work.

    *Why?*: Intra-App features such as shared data services become easy to locate and share from within `app.core` (choose your favorite name for this module).

    Note: This is a strategy for consistency. There are many good options here. Choose one that is consistent, follows Angular's dependency rules, and is easy to maintain and scale.

**[Back to top](#table-of-contents)**

## Modules
### Example
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
###### [Style [S001](#style-s001)]

  - Should always be done! Use [`jsDoc`](http://usejsdoc.org/) syntax to document function names, description, params and returns. Use `@namespace` and `@memberOf` to match your app structure.

    *Why?*: You can generate (and regenerate) documentation from your code, instead of writing it from scratch.

    *Why?*: Provides consistency using a common industry tool.

  - Throughout the examples in this styleguide there is full documentation examples.

### Setting/getting the module
###### [Style [S002](#style-s002)]
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

**[Back to top](#table-of-contents)**

## Services/Factory

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
  - This is an example `productService.js` file. We will go through each part in more detail.

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
###### [See \[Style S001\]](#style-s001)

### Assignment
###### [Style [S003](#style-s003)]
  - To assign a component to angular to be injectable to any other component, you should assign it to it's relating module (eg app.core or product).

    ```javascript
      angular
        .module('product') // Get product module.
        .factory('productFactory', productFactory); // Assign/set productFactory to product module.
    ```

### Injection
###### [Style [S004](#style-s004)]
  - Use `$inject` to manually identify your dependencies for Angular components.

    ```javascript
      productFactory.$inject = [
        '$http',
        'logger',
      ];
    ```

    *Why?*: This technique mirrors the technique used by [`ng-annotate`](https://github.com/olov/ng-annotate), which I recommend for automating the creation of minification safe dependencies. If `ng-annotate` detects injection has already been made, it will not duplicate it.

    *Why?*: This safeguards your dependencies from being vulnerable to minification issues when parameters may be mangled. For example, `common` and `dataservice` may become `a` or `b` and not be found by Angular.

    *Why?*: Avoid creating in-line dependencies as long lists can be difficult to read in the array. Also it can be confusing that the array is a series of strings while the last item is the component's function.

    *Note*: Notice that there is a remaining comma at the end of the Array; this helps with git as only one line changes happen on commits when stuff has been added.

### Organisation
###### [Style [S005](#style-s005)]
  - To adhere to `LIFT` a component should be organised in certain manner, this will provide a cleaner and more maintainable code base. Component structure is done in a way to help with readability, it clearly defines exposure and implementation by seperating the logic/functionality to the bottom of the file. When opening a file you should quickly be able to identify the components implementation into its angular module, its exposed functionality and documentation.

### Exposure and hidden implementation
###### [Style [S006](#style-s006)]
  - The top area of a component should be reserved for defining the exposed details of the component. The bottom half should be used for the implementation details of the component.

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
###### [Style [S007](#style-s007)]
  - In the below code we see that the service returns an object. Can't this be a const (yes), const can contain objects. However objects properties and values can continued to be updated, even as a const that means its not truely a const. As such any object that is likely to update whether its its properties being added removed or values being changed, should be a let to avoid confusion.

    ```javascript
      let service = {
        getData
      };
      return service;
    ```

### Service exception and resolve handling
###### [Style [S008](#style-s008)]
  - Services may handle exception handling to a certain degree. There level of exception handling should be to a level where it handles any updates to data held in the service, and any development logging. Exception handling should not do anything such as displaying a flash message or popup as depending on the use case either could be valid. This should be done in the relevent controller.

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
###### [Style [S009](#style-s009)]

  - Where available use `=>` to define a function that bind the lexical value of `this` to itself, this function is always anonymous. So where you used named functions, use hoisted functions.

    *Note*: [Airbnb style](http://)

    ```javascript
      // Named hoisted function
      function getData() {
        // .then and .catch use anomynous es6 `=>` styled functions.
        return productRestFactory.getData()
          .then((response) => {
            ...
          })
          .catch((error) => {
            ...
          });
      }
    ```

**[Back to top](#table-of-contents)**

## Filters
### Example
  - Avoid using filters for scanning all properties of a complex object graph. Use filters for select properties.

    *Why?*: Filters can easily be abused and negatively affect performance if not used wisely, for example when a filter hits a large and deep object graph.

  - This is an example `productFilter.js` file. We will go through each part in more detail.

    ```javascript
      'use strict';

      angular
        .module('app.core')
        .filter('productFilter', productFilter);

      /**
       * @class Product.Filter
       * @desc A description
       * @memberOf Product
       */
      function productFilter() {
        return filter;

        ///////////

        /**
         * @function filter
         * @desc Filters the product
         * @returns {Promise}
         * @memberOf Product.Filter
         */
        function filter(product) {
          let result = {
            sku: product.sku
          };
          return result;
        }
      }
    ```

### Documentation
###### [See \[Style S001\]](#style-s001)

### Assignment
###### [See \[Style S003\]](#style-s003)
  - As with other components angular assignment should remain the same. Below is the code from above examples, for more information please [see \[Style S003\]](#style-s003).

    ```javascript
      angular
        .module('product') // Get product module.
        .factory('productFitler', productFilter); // Assign/set productFactory to product module.
    ```

### Injection
###### [See \[Style S004\]](#style-s004).
  - As with other components angular injection of dependencies should remain the same style. For more information please [see \[Style S004\]](#style-s004).

### Organisation
###### [See \[Style S005\]](#style-s005)
  - As with other components the organisation/structure should remain the same style. For more information please [see \[Style S005\]](#style-s005).

### Exposure and hidden implementation
###### [See \[Style S006\]](#style-s006)
  - The exposure and hidden implementation based structure should remain the same for all components. For more information please [see \[Style S006\]](#style-s006).

**[Back to top](#table-of-contents)**

## Controllers
  - Please note that controllers should not be used extensively, they are not necessarily a medium of creating logic but an exposure layer between the view and the model.

  - A controller is should only be used with a single directive, and a directive must not be accossiated with more that one controller.

### Example
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
###### [See \[Style S001\]](#style-s001)

### Assignment
###### [See \[Style S003\]](#style-s003)
  - As with other components angular assignment should remain the same style. Below is the code from above examples, for more information please [see \[Style S003\]](#style-s003).

### Injection
###### [See \[Style S004\]](#style-s004)
  - As with other components angular injection of dependencies should remain the same style. For more information please [see \[Style S004\]](#style-s004).

### ES6 Arrow functions
###### [See \[Style [S009\]](#style-s009)

### ControllerAs with vm[CamelCaseName]
###### [Style [Y031](#style-y031)]

  - *See [directives with controllerAs](#style-y075)* for integration of controller (controllerAs) with directives.

  - Use the `controllerAs` syntax over the `classic controller with $scope` syntax.

  - The `controllerAs` syntax uses `this` inside controllers which gets bound to `$scope`

  - It provides a isolated object to the scope. So when you have a controllerAs set to `vmProduct`, that object is placed on your isolated scope as `$scope.vmProduct`. This prevents any cross contamination between directives as they are all completely isolated from each other.

  - Your controllers act as a gateway, they prevent cross contamination to help modulise code, and expose what is needed to the $scope. You may find that you write a little more integration for exposure, but as you write more logic to services you will find the simplicity of the codebase improve dramatically.

  *Why?*: `controllerAs` is syntactic sugar over `$scope`. You can still bind to the View and still access `$scope` methods.

  *Why?*: Helps avoid the temptation of using `$scope` methods inside a controller when it may otherwise be better to avoid them or move the method to a factory, and reference them from the controller. Consider using `$scope` in a controller only when needed. For example when publishing and subscribing events using [`$emit`](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$emit), [`$broadcast`](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$broadcast), or [`$on`](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$on).

### Organisation
###### [See \[Style S005\]](#style-s005)
  - As with other components the organisation/structure should remain the same. For more information please [see \[Style S005\]](#style-s005).

### Exposure and hidden implementation
###### [See \[Style S006\]](#style-s006)
  - The exposure and hidden implementation based structure should remain the same for all components. For more information please [see \[Style S006\]](#style-s006). This use case becomes even more evident with controllers:

    - Place bindable members at the top of the controller, alphabetized, and not spread through the controller code.

      *Why?*: Placing bindable members at the top makes it easy to read and helps you instantly identify which members of the controller can be bound and used in the View.

      *Why?*: Setting anonymous functions in-line can be easy, but when those functions are more than 1 line of code they can reduce the readability. Defining the functions below the bindable members (the functions will be hoisted) moves the implementation details down, keeps the bindable members up top, and makes it easier to read.

    Note: If the function is a 1 liner consider keeping it right up top, as long as readability is not affected.

### Controller focus with logic to Services
###### [Style [Y035](#style-y035)]

  - Defer logic in a controller by delegating to services and factories.

    *Why?*: Logic may be reused by multiple controllers when placed within a service and exposed via a function.

    *Why?*: Logic in a service can more easily be isolated in a unit test, while the calling logic in the controller can be easily mocked.

    *Why?*: Removes dependencies and hides implementation details from the controller.

    *Why?*: Keeps the controller slim, trim, and focused.

  - Define a controller for a view, and try not to reuse the controller for other views. Instead, move reusable logic to factories and keep the controller simple and focused on its view.

    *Why?*: Reusing controllers with several views is brittle and good end-to-end (e2e) test coverage is required to ensure stability across large applications.

### Assigning Controllers
###### [Style [Y038](#style-y038)]

  - When a controller must be paired with a view and either component may be re-used by other controllers or views, define controllers along with their routes.

    *Why?*: Pairing the controller in the route allows different routes to invoke different pairs of controllers and views. When controllers are assigned in the view using [`ng-controller`](https://docs.angularjs.org/api/ng/directive/ngController), that view is always associated with the same controller.

**[Back to top](#table-of-contents)**

## Directives
### Example

  ```javascript
    'use strict';

    angular
      .module('product')
      .directive('productDirective', productDirective);

    productDirective.$inject = [
      'productController',
    ];


    /**
     * @class Product.Directive
     * @desc A description
     * @memberOf Product
     */
    function productDirective(productController) {
      let directive = {
        restrict: 'EA',
        templateUrl: 'path/to/templateUrl',
        scope: {
          // pick up attributes on directive declaration to bindToController
        },
        link: linkFunction,
        controller: productController,
        controllerAs: 'vmProduct',
        bindToController: true
      };

      return directive;

      ///////////

      /**
       * @function linkFunction
       * @desc Product Directive's link function
       * @memberOf Product.Directive
       */
      function linkFunction($scope, $el, $attr, vmProduct) {
        // DOM manipulation should be done in link

        console.log('LINK: $scope.data = %s *** should be undefined', $scope.data);
        console.log('LINK: $scope.vmProduct.data = %s', $scope.vmProduct.data);
        console.log('LINK: vmProduct.data = %s', vmProduct.data);
      }
    }  
  ```

### Cleanup
###### [Style [S010](#style-s010)]
  - "**Best Practice**: Directives should clean up after themselves. You can use `element.on('$destroy', ...)` or `scope.$on('$destroy', ...)` to run a clean-up function when the directive is removed to improve application performance and memory management. This is very important to consider with SPA (as memory can overflow if directives are not correctly removed)

### Manipulate DOM in a Directive
###### [Style [Y072](#style-y072)]

  - When manipulating the DOM directly, use a directive. If alternative ways can be used such as using CSS to set styles or the [animation services](https://docs.angularjs.org/api/ngAnimate), Angular templating, [`ngShow`](https://docs.angularjs.org/api/ng/directive/ngShow) or [`ngHide`](https://docs.angularjs.org/api/ng/directive/ngHide), then use those instead. For example, if the directive simply hides and shows, use ngHide/ngShow.

    *Why?*: DOM manipulation can be difficult to test, debug, and there are often better ways (e.g. CSS, animations, templates)

### Restrict to Elements and Attributes
###### [Style [Y074](#style-y074)]

  - When creating a directive that makes sense as a stand-alone element, allow restrict `E` (custom element) and optionally restrict `A` (custom attribute). Generally, if it could be its own control, `E` is appropriate. General guideline is allow `EA` but lean towards implementing as an element when it's stand-alone and as an attribute when it enhances its existing DOM element.

    *Why?*: It makes sense.

    *Why?*: While we can allow the directive to be used as a class, if the directive is truly acting as an element it makes more sense as an element or at least as an attribute.

    Note: EA is the default with ng 1.3+

### Directives with ControllerAs
###### [Style [Y075](#style-y075)]

  - Use `controller as` syntax with a directive to be consistent with using `controller as` with view and controller pairings.

    Note: The directive below demonstrates some of the ways you can use scope inside of link and directive controllers, using controllerAs. I in-lined the template just to keep it all in one place.

    Note: Note that the directive's controller is outside the directive's closure. This style eliminates issues where the injection gets created as unreachable code after a `return`.


  - Use `bindToController = true` when using `controller as` syntax with a directive when you want to bind the outer scope to the directive's controller's scope.

    *Why?*: It makes it easy to bind outer scope to the directive's controller scope.

    Note: `bindToController` was introduced in Angular 1.3.0.

**[Back to top](#table-of-contents)**

## One Time Binding
###### [Style [S011](#style-S011)]

One time binding can leverage great performance results. In simple form a one time bind de-registers the $watch once it is stable (after the first digest-cycle). This technique is great to reduce complexity in an applications watch and digest cycles to improve an applications responsiveness. For more information see: https://docs.angularjs.org/guide/expression

```html
  <p id="one-time-binding-example">One time binding: {{::name}}</p>
  <p id="normal-binding-example">Normal binding: {{name}}</p>
```

```html
  <p id="one-time-binding-repeat-example" ng-repeat="name in ::names">One time binding: {{name}}</p>
  <p id="normal-binding-repeat-example" ng-repeat="name in ::names">Normal binding: {{name}}</p>
```

**[Back to top](#table-of-contents)**

## Startup Logic
### Configuration
###### [Style [Y170](#style-y170)]

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
###### [Style [Y171](#style-y171)]

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

**[Back to top](#table-of-contents)**

## Angular $ Wrapper Services

### $document and $window
###### [Style [Y180](#style-y180)]

  - Use [`$document`](https://docs.angularjs.org/api/ng/service/$document) and [`$window`](https://docs.angularjs.org/api/ng/service/$window) instead of `document` and `window`.

    *Why?*: These services are wrapped by Angular and more easily testable than using document and window in tests. This helps you avoid having to mock document and window yourself.

### $timeout and $interval
###### [Style [Y181](#style-y181)]

  - Use [`$timeout`](https://docs.angularjs.org/api/ng/service/$timeout) and [`$interval`](https://docs.angularjs.org/api/ng/service/$interval) instead of `setTimeout` and `setInterval` .

    *Why?*: These services are wrapped by Angular and more easily testable and handle Angular's digest cycle thus keeping data binding in sync.

**[Back to top](#table-of-contents)**

## Constants

### Vendor Globals
###### [Style [Y240](#style-y240)]

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

###### [Style [Y241](#style-y241)]

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

**[Back to top](#table-of-contents)**

## Routing
Client-side routing is important for creating a navigation flow between views and composing views that are made of many smaller templates and directives.

###### [Style [Y270](#style-y270)]

  - Use the [AngularUI Router](http://angular-ui.github.io/ui-router/) for client-side routing.

    *Why?*: UI Router offers all the features of the Angular router plus a few additional ones including nested routes and states.

    *Why?*: The syntax is quite similar to the Angular router and is easy to migrate to UI Router.

  *TODO*: Update with examples

###### [Style [Y271](#style-y271)]

  - Define routes for views in the module where they exist. Each module should contain the routes for the views in the module.

    *Why?*: Each module should be able to stand on its own.

    *Why?*: When removing a module or adding a module, the app will only contain routes that point to existing views.

    *Why?*: This makes it easy to enable or disable portions of an application without concern over orphaned routes.

**[Back to top](#table-of-contents)**
