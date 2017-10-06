---
title:  "AngularJS : Requesting JSON data with AJAX"
date: 2017-10-05
author: Ajay Upreti
categories:
- blog
tags:
- frontend
---

In AngularJS you can send AJAX requests in several different ways. These are:

* AJAX calls via the $http service.
* JSONP calls via the $http service.
* REST type calls.

## JSON Data
There are plenty of ways to implement data into your Angular services — some open source and others not so much. For the sake of simplicity, this tutorial will use static JSON files. Here is an example of some mock user data you might want to include in your app:

```
[
    { “name”: “Ankit”, “age” : “26”, “color” : “blue” },
    { “name”: “Sushant”, “age” : “45”, “color”: “black” },
    { “name”: “John”, “age” : “35”, “color”: “brown” }
]
```

## Custom Angular Services and $HTTP

The $http service has several functions you can use to send AJAX requests. These are:

* $http.get(url, config)
* $http.post(url, data, config)
* $http.put(url, data, config)
* $http.delete(url, config)
* $http.head(url, config)

```
(function() {
    
    var app = angular.module(‘modusDemo’);
    app.service(‘userService’, function($http) {
        this.getUsers =function() {
            return $http.get(‘userData.json’);
        }
    })
})();
```

As you can see, `app.service` takes two parameters: a name so we can reference it in our controller, and a function that contains the code our service executes.

`$http` is a core angular service, meaning it comes with Angular right out of the box; there’s no need to define what it does beforehand. According to AngularJS’ own docs, `$http` facilitates communication with remote HTTP servers via the XMLHttpRequest object. In short, if you pass `$http` a URL or local file with the proper response method (in our case `GET`) it will return data from that location.

## Linking to Your Controller and HTML
Now that we have our service, we need to use it. As previously mentioned, our service is now usable throughout our project and we can include it in our controller file. In the same way, we included `$http` in our service, we can include our service in our controller by passing it as an argument. Take a look at the controller setup below:
```
(function() {
    var app = angular.module(‘modusDemo’);
    app.controller(‘todoCtrl’, function(userService) {
        
        var vm = this;
        userService.getUsers().then(function(res){
            console.log(res.data);
            vm.userData = res.data;
        });
    });
})();
```
With `userService` plugged in as an argument, we can now use its methods directly in our controller. After calling the service, it will return data, in this case, our JSON file, and store it in `vm.userData`. After that, it’s as simple as including the controller in your HTML view and using `vm.userData` to display our data via `ng-repeat`. That code looks like this:
```
<body ng-app=”modusDemo” ng-controller=”todoCtrl as user”>
    <h1>Users</h1>
    <div ng-repeat=”users in user.userData”>
        {{users.name}} 
    </div>
</body>
```
And there you have it; using Angular’s existing core functionality we implemented one of Angular’s core services, created our own service, called that service in our controller, and then instantiated the data into our HTML; all while never worrying about writing an API or storing our information to a database. Angular has a lot of awesome services, and using custom services to mock data is only scratching the surface of what they can really do.
