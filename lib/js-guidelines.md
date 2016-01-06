## JavaScript Guidelines
To provide a better code base we will be using [Babel](https://babeljs.io/), this is a ES6 to ES5 compiler. It creates a better code base with stronger structure to code. It has some limitations to what can be converted to ES5 so please take care and fully study babel's guides to understand what can not be easily compiled.

To accompany this guide, it is highly recommended to fully read the [Airbnb JavaScript Guidelines](https://github.com/airbnb/javascript). It provides great insight into improving JavaScript code to make it more maintainable and readable.

### const or let
###### [Style [S-JS001](./js-guidelines.md#s-js001)]
  - In the below code we see that the service returns an object. Can't this be a const (yes), const can contain objects. However objects properties and values can continued to be updated, even as a const that means its not truely a const. As such any object that is likely to update whether its its properties being added removed or values being changed, should be a let to avoid confusion.

    ```javascript
      let service = {
        getData
      };
      return service;
    ```

### ES6 Arrow functions
###### [Style [S-JS002](./js-guidelines.md#s-js002)]

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

**[Back to table of contents](../README.md/#table-of-contents)**
