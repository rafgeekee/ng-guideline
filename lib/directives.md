## Directives

### Example
###### [Style [S-D001](./#s-d001)]

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

### Cleanup
###### [Style [S-D001](./#s-d001)]
  - "**Best Practice**: Directives should clean up after themselves. You can use `element.on('$destroy', ...)` or `scope.$on('$destroy', ...)` to run a clean-up function when the directive is removed to improve application performance and memory management. This is very important to consider with SPA (as memory can overflow if directives are not correctly removed)

### Manipulate DOM in a Directive
###### [Style [Y072](https://github.com/johnpapa/angular-styleguide/#style-y072)]

  - When manipulating the DOM directly, use a directive. If alternative ways can be used such as using CSS to set styles or the [animation services](https://docs.angularjs.org/api/ngAnimate), Angular templating, [`ngShow`](https://docs.angularjs.org/api/ng/directive/ngShow) or [`ngHide`](https://docs.angularjs.org/api/ng/directive/ngHide), then use those instead. For example, if the directive simply hides and shows, use ngHide/ngShow.

    *Why?*: DOM manipulation can be difficult to test, debug, and there are often better ways (e.g. CSS, animations, templates)

### Restrict to Elements and Attributes
###### [Style [Y074](https://github.com/johnpapa/angular-styleguide/#style-y074)]

  - When creating a directive that makes sense as a stand-alone element, allow restrict `E` (custom element) and optionally restrict `A` (custom attribute). Generally, if it could be its own control, `E` is appropriate. General guideline is allow `EA` but lean towards implementing as an element when it's stand-alone and as an attribute when it enhances its existing DOM element.

    *Why?*: It makes sense.

    *Why?*: While we can allow the directive to be used as a class, if the directive is truly acting as an element it makes more sense as an element or at least as an attribute.

    Note: EA is the default with ng 1.3+

### Directives with ControllerAs
###### [Style [Y075](https://github.com/johnpapa/angular-styleguide/#style-y075)]

  - Use `controller as` syntax with a directive to be consistent with using `controller as` with view and controller pairings.

    Note: The directive below demonstrates some of the ways you can use scope inside of link and directive controllers, using controllerAs. I in-lined the template just to keep it all in one place.

    Note: Note that the directive's controller is outside the directive's closure. This style eliminates issues where the injection gets created as unreachable code after a `return`.


  - Use `bindToController = true` when using `controller as` syntax with a directive when you want to bind the outer scope to the directive's controller's scope.

    *Why?*: It makes it easy to bind outer scope to the directive's controller scope.

    Note: `bindToController` was introduced in Angular 1.3.0.

**[Back to table of contents](../README.md/#table-of-contents)**
