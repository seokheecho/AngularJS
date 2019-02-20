# AngularJS API
 - API stands for Application Programming Interface.

## [AngularJS Global API]
 - AngularJS Global API는 다음과 같은 일반적인 작업을 수행하는 전역 JavaScript 함수 집합이다.

  - 객체 비교(Comparing objects)
  - 객체 반복(Iterating objects)
  - 데이터 변환(Converting data)

 - 전역 API 함수는 Anguar 객체(object)를 사용하여 액세스된다.

 - 다음은 몇 가지 일반적인 API 함수 목록이다.
 |API|기술|
 |:-----|:-----|
 |angular.lowercase() | 문자열을 소문자로 변환한다.|
 |angular.uppercase() | 문자열을 대문자로 변환한다.|
 |angular.isString() | 참조가 문자열이면 true를 변환한다.|
 |angular.isNumber() | 참조가 숫자 인 경우 참을 변환한다.|

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>{{ x1 }}</p>
<p>{{ x2 }}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.x1 = "JOHN";
    $scope.x2 = angular.lowercase($scope.x1);
});
</script>
~~~


## [angular.uppercase()]
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
  <p>{{ x1 }}</p>
  <p>{{ x2 }}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.x1 = "John";
  $scope.x2 = angular.uppercase($scope.x1);
});
</script>
~~~


## [angular.isString()]
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
  <p>{{ x1 }}</p>
  <p>{{ x2 }}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.x1 = "JOHN";
  $scope.x2 = angular.isString($scope.x1);
});
</script>
~~~


## [angular.isNumber()]
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
  <p>{{ x1 }}</p>
  <p>{{ x2 }}</p>
</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.x1 = "JOHN";
  $scope.x2 = angular.isNumber($scope.x1);
});
</script>
~~~
