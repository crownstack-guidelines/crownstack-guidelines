---
title:  "My Experiments with AngularJS"
date: 2017-06-30
author: Ajay Upreti
categories:
- blog
tags:
- frontend
---

I have planned to start writing about AngularJS. I have begun to learn AngularJS a few months back, it's a great framework for website UI developers.

* AngularJS version 1.0 was released in 2012.
* Reference for Angular js Tutorial: W3Schools, Tutorialspoint and C# Corner.

### AngularJS Basics

AngularJS is a full featured JavaScript framework, with the core goal of simplification. It excels at building dynamic, single page web apps and supports the Model View Controller (MVC) programming structure. It powers sites include Google, Virgin America, and HBO’s mobile site for iPad. Other highlights:

* Open-source, front-end JavaScript framework developed by Google
* Encourages the developer to use modular building blocks of JavaScript code that can be categorized and are easy to test
* Can be added to any HTML page with a <script> tag

### Tech differentiators of AngularJS include:

* Two-way data bindings

![](https://docs.angularjs.org/img/Two_Way_Data_Binding.png)

* Controllers
* Expressions, which bind data to HTML
* $Scope, a novel way of handling variable dependency and global variables
* Directives, which extend HTML attributes. “Extending” is the key to how AngularJS works

![](https://qph.ec.quoracdn.net/main-qimg-e4fd26b9a1713b64a0f2915bc32527e6.webp)

### Why to use AngularJS

AngularJS gives you everything you need to build the client-side of an application. It will also make it easier to keep your web project organized and modular to avoid repeating code. Advanced features like two-way data binding and dependency injection allow you to quickly create visually stunning and engaging applications that would otherwise take months of development time if you used vanilla JavaScript and jQuery.

* **AngularJS is opinionated.** As a comprehensive client-side solution, AngularJS is naturally opinionated on how a CRUD application should be developed. That means there is definitely an “Angular” way of building a web project, and you’ll need to check with the development team as to whether AngularJS is a right fit for your project’s development workflow.
* **Not all projects require a framework as robust as AngularJS.** For simpler websites, there are lighter weight frameworks like Backbone.js that are better suited to the task.
* **Not suited for data intensive or tricky DOM manipulation.** AngularJS uses “dirty checking” when managing changes to the DOM—the AngularJS digest checks all variables watched by all $scopes for changes. Any value change among any of the variables forces an update of the DOM.

### Best AngularJS world known applications created:

* PayPal
* Netflix
* Weather
* The Guardian
* Lego


### I will describe the components of AngularJS with suitable examples-

AngularJS extends HTML with **ng-directives**.

* **ng-app** − This directive defines and links an AngularJS application to HTML.

* **ng-model** − This directive binds the values of AngularJS application data to HTML input controls.

* **ng-bind** − This directive binds the AngularJS Application data to HTML tags.

**Step 1 − Load framework**

```
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js">
```

**Step 2 − Define AngularJS Application using ng-app directive**

```
<div ng-app = "">
  ...
</div>
```

**Step 3 − Define a model name using ng-model directive**

```<p>Enter your Name: <input type = "text" ng-model = "name"></p>```

**Step 4 − Bind the value of above model defined using ng-bind directive.**

```<p>Hello <span ng-bind = "name"></span>!</p>```

### First AngularJS  Application

```
<html>

   <head>
      <title>First AngularJS  App</title>
   </head>

   <body>
     <h1>Sample Application</h1>

     <div ng-app = "">
         <p>Enter your Name: <input type = "text" ng-model = "name"></p>
         <p>Hello <span ng-bind = "name"></span></p>
     </div>

     <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js">

   </body>
</html>
```
### OUTPUT

![](http://dotnetpattern.com/Images/AngularJS_Sample_Application_UI.png)


### EVERYTHING CHANGES WITH ANGULAR 2.0

* **Angular 2 is based entirely on components**—say goodbye to $scope and controllers, and hello to @components, Angular’s latest take on the dependency injection model. A component is basically a directive with a template.
* **Streamlined directives**—Creating your own directives has gotten even easier with the new @Directive annotation, simply set your selector, properties, and host listeners.
* **ECMAScript 6 (ES6)**—Angular 2.0 supports the latest JavaScript standard.
* **Support for TypeScript**— great news for.NET developers, Microsoft’s open-source extension to ES6 will be supported by Angular 2. That means you get access to all the advantages, libraries, and technologies associated with TypeScript.
