# AngularJS Scope
 - `scope` 은 HTML(View)과 JavaScript(Controller) 간의 바인딩 부분이다.
 - `scope` 은 사용 가능한 변수(properties)와 메서드(methods)를 가진 객체이다.
 - `scope` 은 뷰(View)와 컨트롤러(Controller)에서 모두 사용 가능하다.


## [How to Use the Scope?]
 - AngularJS에서 컨트롤러를 만들 때, $scope객체를 인수(argument)로 전달</br>

 - 컨트롤러에서 만들어진 속성(Properties)은 뷰에서 참조 할 수 있다.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.carname = "Volvo";
});
</script>
<p>The property "carname" was made in the controller, and can be referred to in the view by using the {{ }} brackets.</p>
~~~

 - `$scope` 컨트롤러의 객체에 속성(properties)을 추가할 때, View(HTML)에서 그 속성(properties)에 액세스 할 수 있다.
 - 뷰(View)에서 접두어 `$scope`를 사용하지 않고, 단지 propertyname을 참조해라! 이거와 같이 `{{carname}}`


## [Understanding the Scope]
 - AngularJS application이 다음으로 구성되어 있다고 생각될 경우 :
 - 1) View, HTML 이다.
 - 2) Model, 현재 뷰(view)에서 사용 가능한 데이터이다.
 - 3) Controller, 데이터를 변경/제거/제어하는 ​​JavaScript 함수이다.
 - 이후 `scope`은 모델이다.
 - `scope`은 변수(properties)와 메서드(methods)를 가진 JavaScript 객체이며, View와 Controller에서 모두 사용할 수 있다.</br>

 - View 를 변경하면 Model과 Controller가 업데이트된다.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<input ng-model="name">
<h1>My name is {{name}}</h1>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.name = "John Doe";
});
</script>
<p>When you change the name in the input field, the changes will affect the model, and it will also affect the name property in the controller.</p>
~~~


## [Know Your Scope]
 - 언제든지 어떤 `scope`을 다루고 있는지를 아는 것이 중요하다!
 - 위의 두 예제에는 하나의 `scope`만 있으므로 `scope`을 아는 것은 문제가되지 않지만, 큰 application의 경우 HTML DOM에 특정 `scope`에만 액세스 할 수 있는 섹션이 있을 수 있다.</br>

 - `ng-repeat` 지시어를 처리 할 때, 각 반복은 현재 반복 객체(repetition object)에 액세스 할 수 있다.
 (When dealing with the ng-repeat directive, each repetition has access to the current repetition object:)
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<ul>
  <li ng-repeat="x in names">{{x}}</li>
</ul>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.names = ["Emil", "Tobias", "Linus"];
});
</script>
<p>The variable "x" has a different value for each repetition, proving that each repetition has its own scope.</p>
~~~

 - 각 <li>요소는 현재 반복 객체(repetition object)에 액세스 할 수 있다.
 - 이 경우에는 반복 객체(repetition object)를 사용하여 참조되는 문자열 x이다.


## [Root Scope]
 - 모든 application에는 `ng-app` 지시어가 포함된 HTML 요소에 생성된 `scope`인 `$rootScope`가 있다.

 - `rootScope`은 전체 application에서 사용할 수 있다.\

 - 변수가 현재 scope과 rootScope에서 동일한 이름을 갖는 경우 application은 현재 scope에 있는 변수를 사용한다.
 (If a variable has the same name in both the current scope and in the rootScope, the application uses the one in the current scope.)</br>

 - "color"라는 변수는 controller's scope과 rootScope에 둘 다 존재한다. :
~~~HTML
<body ng-app="myApp">
<p>The rootScope's favorite color:</p>
<h1>{{color}}</h1>
<div ng-controller="myCtrl">
  <p>The scope of the controller's favorite color:</p>
  <h1>{{color}}</h1>
</div>
<p>The rootScope's favorite color is still:</p>
<h1>{{color}}</h1>
<script>
var app = angular.module('myApp', []);
app.run(function($rootScope) {
  $rootScope.color = 'blue';
});
app.controller('myCtrl', function($scope) {
  $scope.color = "red";
});
</script>
<p>Notice that controller's color variable does not overwrite the rootScope's color value.</p>
</body>
~~~

~~~HTML
The rootScope's favorite color:

blue
The scope of the controller's favorite color:

red
The rootScope's favorite color is still:

blue
Notice that controller's color variable does not overwrite the rootScope's color value.
~~~
