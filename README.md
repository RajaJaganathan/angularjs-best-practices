# Angularjs-best-practices
#####My favourite angularjs developement  best practices :


1. use controller as syntax. Never pollute any value on $scope/scope

2. Always use bindToController when using isolate scope

3. Use fully controller as syntax like at $scope.$watch(vm.foo, function(){});

4. Use $digest methods instead of $apply when ever possible

5. In controller never attached to variable and method which are not used in angular template

6. Use directive controller as API

7. Controller should not aware of business logic and should be thin as much as possible

8. Controller shouldn't be shared with any service/controller etc..,

9. Never use $parent().$parent() it hard to test it will break if we use ng-if, ng-include since it introduce new scope

10. Use ng-message-exp for dynamic validation fields

11. Use one way binding when ever possible.

12. Setup environment variable like devlopment production configuration path,mode by using gulp-ng-constants plugin
