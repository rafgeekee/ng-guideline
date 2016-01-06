## Binding

### One Time Binding
###### [Style [S-B001](./#s-b001)]

One time binding can leverage great performance results. Simply one time binding de-registers the associated $watch once the bind is stable, after the first digest-cycle. This technique is great to reduce complexity in an applications watch and digest cycle to improve responsiveness. For more information see: https://docs.angularjs.org/guide/expression

```html
  <p id="one-time-binding-example">One time binding: {{::name}}</p>
  <p id="normal-binding-example">Normal binding: {{name}}</p>
```

```html
  <p id="one-time-binding-repeat-example" ng-repeat="name in ::names">One time binding: {{name}}</p>
  <p id="normal-binding-repeat-example" ng-repeat="name in names">Normal binding: {{name}}</p>
```

**[Back to table of contents](../README.md/#table-of-contents)**
