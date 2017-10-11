#Use controllerAs syntax instead of classic (older) $scope object

##controllerAs View Syntax

WHY...?

- Controllers are constructed, "newed" up, and provide a single new instance, and the controllerAs syntax is closer to that of a JavaScript constructor than the classic $scope syntax.

  - It promotes the use of binding to a "dotted" object in the View (e.g. customer.name instead of name), which is more contextual, easier to read, and avoids any reference issues that may occur without "dotting".
  - It helps avoid using $parent calls in Views with nested controllers.

<!-- avoid -->
'''<div ng-controller="CustomerController">
    {{ name }}
</div>'''
<!-- recommended -->
<div ng-controller="CustomerController as customer">
    {{ customer.name }}
</div>

#Use controllerAs syntax instead of classic (older) $scope object

##controllerAs Controller Syntax

- The controllerAs syntax uses this inside controllers which gets bound to $scope

  - controllerAs is syntactic sugar over $scope. You can still bind to the View and still access $scope methods.
  - Helps avoid the temptation of using $scope methods inside a controller when it may otherwise be better to avoid them or move the method to a factory, and reference them from the controller. Consider using $scope in a controller only when needed. For example when publishing and subscribing events using $emit, $broadcast
