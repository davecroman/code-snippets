## Core Directives

* `ng-app`

>```
<html ng-app="store">
```

* `ng-controller`

>```
<body ng-controller="StoreController as store">
```

## Built-in Directives

* ng-show

>```
ng-show="product.shouldShow"
```

* ng-hide

>```javascript
ng-hide="product.isHidden"
```


* ng-repeat

>``` ng-repeat="product in store.products" ```

* ng-src

>```
<img ng-src="{{product.images[0].full}}"/>
```

* ng-click
* ng-init

>``` ng-init="tab = 1"```

* ng-class

>```ng-class = "{ active:tab ===3 }"```


* ng-model //data-binding
* ng-submit 

>```ng-submit="ctrl.addReview(product)"```

## Custom Directives // for expressive html documents

### Types of custom directives:
1. Element directives
`<product-title></product-title>  // do not use self closing tag because not all browsers like it, self-closing tags look like this: <p/>`
2. Attribute Directive
<h3 product-title></h3>

### Element directive

```javascript
app.directive('productTitle', function() {
    return { //this is a directive definition object, i.e., a configuration
        restrict: 'E', //element
        templateUrl: 'product-title.html' //url of template
    };
});
```

Usage:
```
<product-title></product-title> //dash translates to camel case, hence productTitle
```

### Attribute directive
```javascript
app.directive('productTitle', function() {
    return { //this is a directive definition object, i.e., a configuration
        restrict: 'A', //attribute
        templateUrl: 'product-title.html' //url of template
    };
});
```

### Directive Controllers
```javascript
app.directive('productTitle', function() {
    return { //this is a directive definition object, i.e., a configuration
        restrict: 'E', //element
        templateUrl: 'product-title.html',
        controller: function() {
        ...},
        controllerAs: 'panels'
    };
});
```

## Grouping directives into one module

1. Create a new .js file
2. Put all relevant directives into it, name its module
3. On your main directive, declare a dependency to the module you created in (2) by adding its name to the array parameter in angular.module('', [])
4. Add the new js file into the scripts tag of the html file

