## Organisation and Documentation

### JSDOC
###### [Style [S-OD001](./#s-od001)]

  - Should always be done! Use [`jsDoc`](http://usejsdoc.org/) syntax to document function names, description, params and returns. Use `@namespace` and `@memberOf` to match your app structure.

    *Why?*: You can generate (and regenerate) documentation from your code, instead of writing it from scratch.

    *Why?*: Provides consistency using a common industry tool.

  - Throughout the examples in this guideline there is full documentation examples.


### Organisation
###### [Style [S-OD002](./#s-od002)]

  - To adhere to `LIFT` a component should be organised in certain manner, this will provide a cleaner and more maintainable code base. Component structure is done in a way to help with readability, it clearly defines exposure and implementation by separating the logic/functionality to the bottom of the file. When opening a file you should quickly be able to identify the components implementation into its angular module, its exposed functionality and documentation.

### Exposure and hidden implementation
###### [Style [S-OD003](./#s-od003)]

  - The top area of a component should be reserved for defining the exposed details of the component.

  - The bottom half should be used for the implementation details of the component.

  - Place exposed members at the top of the component, alphabetized, and not spread through the component code.

    *Why?*: Placing exposed members at the top makes it easy to read and helps you instantly identify which members are being exposed by the component.

    *Why?*: Setting anonymous functions in-line can be easy, but when those functions are more than 1 line of code they can reduce the readability. Defining the functions below the exposed members (the functions will be hoisted) moves the implementation details down, keeps the exposed members up top, and makes it easier to read.

    Note: If the function is a 1 liner consider keeping it right up top, as long as readability is not affected.

  ```javascript
    /**
     *
     * documentation
     *
     */
    function productFactory() {
      let result = {
        fn,
        fn2,
        fn3,
      };
      return result;

      ///////////

      /**
       *
       * documentation
       *
       */
      function fn() {
        // gets data
      }

      /**
       *
       * documentation
       *
       */
      function fn2() {
        // gets data
      }

      /**
       *
       * documentation
       *
       */
      function fn3() {
        // gets data
      }
    }
  ```


**[Back to table of contents](../README.md/#table-of-contents)**
