# AngularJS Data Binding
 - AngularJS 에서 데이터 바인딩(Data Binding)은 모델(Modle)과 뷰(View) 간의 동기화이다.

## [Data Model]
 - AngularJS applications은 대개 데이터 모델을 가지고 있다. 데이터 모델은 application에서 사용할 수 있는 데이터 모음이다.

~~~javascript
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.firstname = "John";
  $scope.lastname = "Doe";
});
~~~

## [HTML View]
 - AngularJS applications에서 표시되어지는 HTML 컨테이너(Container)는 뷰(View)라고 부른다.
 - 뷰(View)는 모델(Model)에 대한 액세스 권한이 있으며, 뷰(View)에 모델 데이터(model data)를 표시하는 데는 여러가지 방법이 있다.
 - `ng-bind` 지시어를 사용하면 innerHTML의 요소를 지정된 모델 속성으로 바인딩 할 수 있다.

~~~HTML
<body>
<div ng-app="myApp" ng-controller="myCtrl">
    <p ng-bind="firstname"></p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.firstname = "John";
    $scope.lastname = "Doe";    
});
</script>
<p>Use the ng-bind directive to bind the innerHTML of an element to a property in the data model.</p>
</body>
~~~

 - 이중 중괄호(`{{ }}`)를 사용 하여 모델의 내용을 표시 할 수도 있다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
    <p>First name: {{firstname}}</p>
</div>
~~~

 - 또는 HTML 컨트롤의 `ng-model` 지시어를 사용하여 모델을 뷰에 바인딩 할 수 있다.

~~~HTML
<body>
<div ng-app="myApp" ng-controller="myCtrl">
    <p>First name: {{firstname}}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.firstname = "John";
    $scope.lastname = "Doe";    
});
</script>
<p>You can use double braces to display content from the data model.</p>
</body>
~~~

## [The ng-model Directive]
 - `ng-model` 지시문을 사용하여 모델의 데이터(data model)를 HTML 컨트롤의 뷰(View)에 바인딩한다. (input, select, textarea).

~~~HTML
<input ng-model="firstname">
~~~

 - `ng-model` 지시문은 모델(Model)과 뷰(View) 간에 양방향 바인딩을 제공한다.


## [Two-way Binding]
 - AngularJS 에서 데이터 바인딩(Data Binding)은 모델(Modle)과 뷰(View) 간의 동기화이다.

 - When data in the model changes, the view reflects the change, and when data in the view changes, the model is updated as well. This happens immediately and automatically, which makes sure that the model and the view is updated at all times.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
  Name: <input ng-model="firstname">
  <h1>{{firstname}}</h1>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.firstname = "John";
  $scope.lastname = "Doe";
});
</script>
~~~


## [AngularJS Controller]
 - AngularJS의 Applications 은 컨트롤러에 의해 제어된다. AngularJS Controllers Chapter에서 컨트롤러에 대해 읽어보자.

 - Because of the immediate synchronization of the model and the view, the controller can be completely separated from the view, and simply concentrate on the model data. Thanks to the data binding in AngularJS, the view will reflect any changes made in the controller.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
  <h1 ng-click="changeName()">{{firstname}}</h1>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.firstname = "John";
  $scope.changeName = function() {
    $scope.firstname = "Nelly";
  }
});
</script>
~~~
