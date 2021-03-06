# Angularjs-best-practices


### Angularjs General Guideline:

* Use always controller as syntax and never pollute any value/property on $scope/scope property.

* Don't pollute any variables and methods on controller vm and $scope which is not used from template/views.

* Always use bindToController when using isolate scope for directive api.

* Always enable ng-strict-di so that minification won't surprise at last moment.

* Always use component instead of directive whenever possible. Following sceneraio are not fit in component api, ie, DOM manipulatation, Dynamic template compilation, restrict to attrs/class

```javascript

        angular.component('counter', {
            bindings: {
                count: '<'
            },
            controller: function() {}
        }
```

* Always use controller as syntax like at $scope.$watch(vm.foo, function(){});

* In order to avoid number of variable declaration, group by features by using object literal syntax.

```javascript
        var firstName = 'John';
        var lastName = 'Doe';
        var age = 30;
```

```javascript
        var person = {
                firstName:'John',
                lastName:'Doe',
                age:30
        };
```

* Use directive controller as API for directive.

* At any point time, controller should not aware of any business logic and should be thin as much as possible.

* Angular services such as Factory/Service/Provider/Const/Value should follow single responsility priniclple.

* Controller should not be shared with any factory, service and even other controller etc..,

* Never use $parent().$parent() it hard to test it will break if we use ng-if, ng-include, ng-switch since it will introduce new scope.

* Use ng-message-exp for dynamic validation fields

* Use Angular Batarang and ng-inspector browser plugin for improve our development productivity.

* Filter angular@1.3: Store filtered result with help of 'as' syntax in ng-repeat like ```<div ng-repeat="person in data | filter:query as results"></div> {{results.length}}``` 

### Angular 1.x Performance Guidelines:

* Always use one way binding by using ng-bind directive, binding expression like 

```javascript

    {{::variableName}}
    
    ng-class="::{'btn-success':vm.isSucceed}"
    
    ng-repeat="item in ::items"
```

* Avoid angular filter expression as much as possible. Instead invoke filter in controller. Costly operation because every single digest cycle filter invoked twice.

* Use ng-if instead of ng-show/ng-hide whenever possible, angular does dirty checks for hidden elements too.

* Always use 'track by' expression with ng-repeat to improve a performance. Use $index when collection has no unique fields.

```javascript
        <div ng-repeat="model in collection track by model.id">
          {{model.name}}
        </div>
        
        <div ng-repeat="item in dataSource track by $index">  
        </div>

```

* Use $watchCollection instead $watch with deep comparision flag whenever possible.

* Use ngModelOptions and also inherited for all form fields so defer the digest cycle.

```javascript

        ng-model-options={
          updateOn: 'default blur',
          debounce: { 'default': 500, 'blur': 0 }
        };

```
* Use $destroy to remove the event listeners from DOM and scope.

```javascript
        scope.$on("$destroy", function() {
            element.off('click', windowClick);    
            scope.$off('modalOpened',onModelOpened);
       });

```
* Use component instead of directives with one way data binding.
``` javascript
        angular.component('counter', {
            bindings: {
                count: '<'
            },
            controller: function() {}
        }
```      

* Use $digest methods instead of $apply when ever possible reason behind that when don't want trigger all digest cycle to up $rootScope.

* Multiple XHR call that triggers multiple digest cycle to avoid optimize this cycle 
 
```javascript
    app.config(function ($httpProvider) {
      $httpProvider.useApplyAsync(true);
    });
```

* Use asynEval in directive link method for initialize jquery plugins and get performance improvement.(http://www.bennadel.com/blog/2635-looking-at-how-scope-evalasync-affects-performance-in-angularjs-directives.htm)

* Use angular-watcher chrome extension for find how many watcher used in application.

* Disable debug information in production
```javascript
    app.config(function ($compileProvider) {
      $compileProvider.debugInfoEnabled(false);
    }]);
```

* Avoid using $emit, $broadcast on $scope/$rootScope instead use event emitter libs such as Postal, Event Emitter, etc.

```javascript
app.const('appChannel', new EventEmitter());
```

* Use angular translate once(https://github.com/ajwhite/angular-translate-once/blob/develop/src/translate-once.js) libary in order to avoid massive $watcher in application. 
