## Angular Dependency Injection

### Module assignment
###### [Style [S-DA001](./#s-da001)]

  - To assign a component to angular to be injectable to any other component, you should assign it to it's relating module (eg app.core or product).

  - *Why?*: Angular comes with dependency injection, therefore removing much need for having module loaders such as `Require.js`.  When using angular you can set a module like `angular.[module type]('module name', module)`:

    ```javascript
      angular
        .module('product') // Get product module.
        .factory('productFactory', productFactory); // Assign/set productFactory to product module.
    ```

### Dependency Injection
###### [Style [S-DA002](./#s-da002)]

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
