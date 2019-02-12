# AngularJS Controllers
 - AngularJS 에서 컨트롤러(Controller)는 AngularJS application의 data를 제어한다.
 - AngularJS 컨트롤러는 일반 JavaScript 객체이다.

## [AngularJS Controllers]
 - AngularJS의 applications 는 컨트롤러에 의해 제어된다.
 - `ng-controller` 지시어는 application controller 를 정의한다.
 - 컨트롤러는 표준 JavaScript의 객체생성자에 의해 생성된 JavaScript 객체이다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{firstName + " " + lastName}}
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.firstName = "John";
  $scope.lastName = "Doe";
});
</script>
~~~

application 설명 :

- 1) AngularJS application 은 ng-app = "myApp" 로 정의된다. application은 <div> 내부에서 실행된다.
- 2) `ng-controller="myCtrl"` 속성은 AngularJS 지시자(directive)이다. 그것은 컨트롤러를 정의한다.
- 3) myCtrl의 function은 JavaScript function 이다.
- 4) AngularJS는 $scope 객체로 컨트롤러를 호출한다.
- 5) AngularJS에서 $scope는 application 객체이다.(application 변수와 함수의 소유자(owner))
- 6) 컨트롤러는 두 개의 속성(변수)를 scope(firstName과 lastName)안에 만든다.
- 7) `ng-model` 지시자는 input 필드로 controller 변수(firstName과 lastName)를 바인딩한다.


## [Controller Methods]
 - 위 예제는 두 개의 변수(lastName과 firstName)를 가진 컨트롤러 객체를 보여준다.
 - 컨트롤러는 메소드(변수 이뤄진 함수들)를 가질 수도 있다.

~~~HTML
<div ng-app="myApp" ng-controller="personCtrl">
First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{fullName()}}
</div>
<script>
var app = angular.module('myApp', []);
app.controller('personCtrl', function($scope) {
  $scope.firstName = "John";
  $scope.lastName = "Doe";
  $scope.fullName = function() {
    return $scope.firstName + " " + $scope.lastName;
  };
});
</script>
~~~


## [Controllers In External Files]
 - 대규모 application에서는 컨트롤러를 외부 파일에 저장하는 것이 일반적이다.
 - <script> 태그 사이의 코드를 personController.js 라는 외부 파일로 복사하자.

~~~HTML
<div ng-app="myApp" ng-controller="personCtrl">
First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{fullName()}}
</div>
<script src="personController.js"></script>
~~~


## [Another Example]
 - 다음 예제에서는 새 컨트롤러 파일을 만든다.

~~~javascript
angular.module('myApp', []).controller('namesCtrl', function($scope) {
  $scope.names = [
    {name:'Jani',country:'Norway'},
    {name:'Hege',country:'Sweden'},
    {name:'Kai',country:'Denmark'}
  ];
});
~~~
 - namesController.js로 파일을 저장하자.
 - 그런 다음 application에서 컨트롤러 파일을 사용해 보자.

~~~HTML
<div ng-app="myApp" ng-controller="namesCtrl">
<ul>
  <li ng-repeat="x in names">
    {{ x.name + ', ' + x.country }}
  </li>
</ul>
</div>
<script src="namesController.js"></script>
~~~
