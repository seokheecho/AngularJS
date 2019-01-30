# AngularJS Modules
 - AngularJS 모듈은 application을 정의한다.
 - 모듈은 application의 다른 여러 부분을 담는 컨테이너이다.
 - 모듈은 application 제어(controllers)들을 위한 컨테이너이다.
 - 컨트롤러는 항상 모듈에 속한다.


## [Module 만들기]
 - AngularJS 함수를 사용하여 모듈을 만든다. `angular.module`
~~~HTML
<div ng-app="myApp">...</div>
<script>
    var app = angular.module("myApp", []);
</script>
~~~
 - "myApp" parameter는 application이 실행될 HTML 요소를 참조한다.
 - 이제 컨트롤러, 지시문, 필터 등을 AngularJS application에 추가 할 수 있다.


## [Controller 추가]
 - Application에 Controller를 추가하고, `ng-controller` 지시문(directive)을 사용하는 Controller를 참조하자.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
{{ firstName + " " + lastName }}
</div>
<script>
    var app = angular.module("myApp", []);
    app.controller("myCtrl", function($scope) {
      $scope.firstName = "John";
      $scope.lastName = "Doe";
    });
</script>
~~~


## [지시어(Directive) 추가]
 - AngularJS에는 application에 기능을 추가하는 데 사용할 수있는 내장 지시어(Directive) 세트가 있다.
 - 자세한 내용은 AngularJS 지시어(Directive)를 참조 <br/>
  참조 : https://www.w3schools.com/angular/angular_ref_directives.asp
 - Module를 사용하여 application에 직접 지시어(Directive)를 추가 할 수 있다.
~~~HTML
<div ng-app="myApp" w3-test-directive></div>
<script>
    var app = angular.module("myApp", []);
    app.directive("w3TestDirective", function() {
      return {
        template : "I was made in a directive constructor!"
      };
    });
</script>
~~~


## [Modules and Controllers in Files]
 - AngularJS application에서는 Module과 Controller를 JavaScript 파일에 두는 것이 일반적이다.
 - 이 예제에서 "myApp.js"는 응용 프로그램 Module 정의를 포함하고 "myCtrl.js"는 Controller를 포함한다.

~~~HTML
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="myCtrl">
{{ firstName + " " + lastName }}
</div>

<script src="myApp.js"></script>
<script src="myCtrl.js"></script>

</body>
</html>
~~~

 - myApp.js
~~~JavaScript
var app = angular.module("myApp", []);
~~~
** Module 정의의 [] parameter를 사용하여 dependent modules(종속모듈)을 정의 할 수 있다. </br>
[] parameter가 없으면 new module을 만들지 않고 기존 모듈을 검색한다. </br>

 - myCtrl.js
~~~JavaScript
app.controller("myCtrl", function($scope) {
  $scope.firstName = "John";
  $scope.lastName= "Doe";
});
~~~


## [Functions can Pollute the Global Namespace]
 - 전역 함수는 JavaScript에서 피해야한다. 다른 스크립트로 쉽게 덮어 쓰거나 파괴 할 수 있다.
 - AngularJS Module은 모든 함수를 Module에 local로 유지함으로써 이 문제를 줄인다.


## [Library 로드(load) 시기]
 - `<body>` 요소 의 끝에 스크립트를 배치하는 것은 HTML application에서 일반적이지만, `<head>` 또는 시작 부분 에 AngularJS 라이브러리를 로드하는 것이 좋다.

 - 라이브러리가 로드 된 후에 만 angular.module을 호출하여 컴파일 할 수 있기 때문이다.

~~~HTML
<!DOCTYPE html>
<html>
<body>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>

<div ng-app="myApp" ng-controller="myCtrl">
{{ firstName + " " + lastName }}
</div>

<script>
    var app = angular.module("myApp", []);
    app.controller("myCtrl", function($scope) {
        $scope.firstName = "John";
        $scope.lastName = "Doe";
    });
</script>

<p>It is recommended that you load the AngularJS library either in the HEAD or at the start of the BODY.</p>

</body>
</html>
~~~
