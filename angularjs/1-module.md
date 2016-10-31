# AngularJS Notes 

[Published version](http://simp.ly/publish/5BQWn0)

## Creating a Module

```javascript
var app = angular.module("store", []);
```

## Creating a controller
```javascript
app.controller("NameOfController", function() {
	// do something
});
```








## Grouping directives into one module

1. Create a new .js file
2. Put all relevant directives into it, name its module
3. On your main directive, declare a dependency to the module you created in (2) by adding its name to the array parameter in angular.module('', [])
4. Add the new js file into the scripts tag of the html file

## Services

They begin with a dollar sign because they are built-in in angular.

Example:

```  
app.controller('StoreController', ['$http', function($http){  

    var store = this;  
    store.products = [];  
    
    $http.get('/store-products.json').success(function(data){  
      store.products = data;  
    });  
      
  }]);  

```