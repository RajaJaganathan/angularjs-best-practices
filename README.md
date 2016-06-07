# Angularjs-best-practices
#####My favourite tips for angularjs developement:


* Use always controller as syntax and never pollute any value/property on $scope/scope property.

* Don't pollute variables and methods on controller' vm and $scope which are not used/accessed from views.

* Always use bindToController when using isolate scope

* Always use controller as syntax like at $scope.$watch(vm.foo, function(){});

* Use $digest methods instead of $apply when ever possible.

* Use directive controller as API for component

* At any point controller should not aware of any business logic and should be thin as much as possible and should Obey(SRP)

* Controller should n't be shared with any factory/service/other controller etc..,

* Never use $parent().$parent() it hard to test it will break if we use ng-if, ng-include since it introduce new scope

* Use ng-message-exp for dynamic validation fields

* Use one way binding when ever possible by using ng-bind and {{::variableName}}

* Setup environment variable like devlopment production configuration path,mode by using gulp-ng-constants plugin

* Use Angular Batarang and ng-inspector browser plugin for improve our development productivity.

* Use asynEval in directive link method for initialize jquery plugins and get performance improvement.(http://www.bennadel.com/blog/2635-looking-at-how-scope-evalasync-affects-performance-in-angularjs-directives.htm)

* Filter angular@1.3: Store filtered result with help of 'as' syntax in ng-repeat like ```<div ng-repeat="person in data | filter:query as results"></div> {{results.length}}``` 
