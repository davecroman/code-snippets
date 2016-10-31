## Services

They begin with a dollar sign because they are built-in in angular.

Example:

```javascript
app.controller('StoreController', ['$http', function($http){  

    var store = this;  
    store.products = [];  
    
    $http.get('/store-products.json').success(function(data){  
      store.products = data;  
    });  
      
  }]);  

```