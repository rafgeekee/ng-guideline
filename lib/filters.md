## Filters

  - Avoid using filters for scanning all properties of a complex object graph. Use filters for select properties.

    *Why?*: Filters can easily be abused and negatively affect performance if not used wisely, for example when a filter hits a large and deep object graph.

### Example
###### [Style [S-F001](./#s-f001)]

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
###### [See \[Style S-OD001\]](./organisation-documentation.md#s-od001)

### Organisation
###### [See \[Style S-OD002\]](./organisation-documentation.md#s-od002)

### Exposure and hidden implementation
###### [See \[Style S-OD003\]](./organisation-documentation.md#s-od003)

### Assignment
###### [See \[Style S-DA001\]](./di-assignment.md#s-da001)

### Dependency Injection
###### [See \[Style S-DA002\]](./di-assignment.md#s-da002)


**[Back to table of contents](../README.md/#table-of-contents)**
