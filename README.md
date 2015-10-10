# Angularjs-best-practices
My favourite angularjs developement  best practices


use controller as syntax. Never pollute any value on $scope/scope

Always use bindToController when using isolate scope

Use fully controller as syntax like at $scope.$watch(vm.foo, function(){});

Use $digest methods instead of $apply when ever possible

In controller never attached to variable and method which are not used in angular template

Use directive controller as API

Controller should not aware of business logic and should be thin as much as possible

Controller shouldn't be shared with any service/controller etc..,

Never use $parent().$parent() it hard to test it will break if we use ng-if, ng-include since it introduce new scope

Use ng-message-exp for dynamic validation fields

Use one way binding when ever possible.

Setup environment variable like devlopment production configuration path,mode by using gulp-ng-constants plugin
