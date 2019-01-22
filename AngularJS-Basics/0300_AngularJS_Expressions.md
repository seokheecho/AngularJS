# AngularJS Expressions
AngularJS는 표현식(Expressions)을 사용하여 HTML에 데이터를 바인딩한다.

## [AngularJS 표현식(Expressions)]
 - AngularJS expression은 이중 중괄호 안에 쓸 수 있다. `{{ expression }}`
 - AngularJS expression은 지시문 안에도 쓸 수 있다. `ng-bind="expression"`
 - AngularJS 는 표현식(Expressions)을 해결하고 표현식(Expressions)이 쓰여지는 곳의 결과를 정확하게 반환한다.
 - AngularJS 표현식(Expressions)은 JavaScript 표현식(Expressions)과 매우 유사하다. 리터럴, 연산자 및 변수를 포함 할 수 있다. ex) {{5 + 5}} 또는 {{firstName + ""+ lastName}}

### 예제
~~~HTML
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
  <p>My first expression: {{ 5 + 5 }}</p>
</div>

</body>
</html>
~~~

 - ng-app 지시문을 제거하면 HTML은 해결하지 않고 그대로 표현식을 표시
~~~HTML
<div>
    <p>My first expression: {{ 5 + 5 }}</p>
</div>
~~~

 - 원하는 위치에 표현식을 쓸 수 있으며, AngularJS는 표현식을 해결하고 결과를 반환한다. </br>
ex) AngularJS가 CSS 속성 값을 변경하도록한다.

 - 값을 변경하여 아래 입력 상자의 색상을 변경
~~~html





















  AngularJS는 JavaScript Framework <br/>
`<script>` 태그를 사용하여 HTML 페이지에 추가 할 수 있다. <br/>
AngularJS는 지시어(Directives)로 HTML 속성을 확장하고 표현식(Expressions)으로 HTML에 데이터를 바인딩한다. <br/>

** 데이터 바인딩(Data Binding) <br/>
  데이터 바인딩 이란 두 데이터 혹은 정보의 소스를 모두 일치시키는 기법이다. <br/>
즉 화면에 보이는 데이터와 브라우저 메모리에 있는 데이터를 일치시키는 기법 <br/>
 - 참고 : https://sungjk.github.io/2015/11/22/AngularJS(2).html


## [AngularJS는 JavaScript 프레임 워크]
  JavaScript로 작성된 라이브러리이다. <br/>
AngularJS는 JavaScript 파일로 배포되며 스크립트 태그가 있는 웹 페이지에 추가 할 수 있다. <br/>

<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>


## [AngularJS는 HTML을 확장]
  AngularJS는 ng-directives로 HTML을 확장 <br/>
 - ng-app 지시어(directive)는 AngularJS application 임을 정의한다.
 - ng-model 지시어(directive)는 application data로 HTML 제어 값(input, select, textarea)을 바인딩한다.
 - ng-bind 지시어(directive)은 HTML보기로 application data를 바인딩한다.

### 예제
~~~html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
    <p>Name: <input type="text" ng-model="name"></p>
    <p ng-bind="name"></p>
</div>

</body>
</html>
~~~
Example explained:
 1) AngularJS는 웹 페이지가 로드 될 때 자동으로 시작
 2) ng-app 지시어는 '`<div>` 요소'의 owner of an AngularJS application.
 3) ng-bind 지시어는 'application variable name'으로 '`<p>` 요소의 내용(content)'을 바인딩


## [AngularJS 지시문(Directives)]
 - ng-app : AngularJS application 임을 정의
 - ng-init : AngularJS application 변수들을 초기화
 - data-ng- : HTML page를 유효하게 하려면 ng- 대신 data-ng- 를 사용

 ** HTML 유효성 검사(왜 유효성 검사를 하는가?)
 - 참고 : http://www.clearboth.org/24_validating_your_html/

### 예제
~~~html
<div ng-app="" ng-init="firstName='John'">
    <p>The name is <span ng-bind="firstName"></span></p>
</div>
~~~
~~~html
<div data-ng-app="" data-ng-init="firstName='John'">
    <p>The name is <span data-ng-bind="firstName"></span></p>
</div>
~~~


## [AngularJS 표현식(Expressions)]
  AngularJS 표현식(expression)은 이중 중괄호 {{expression}} 안에 작성된다. <br/>
AngularJS는 표현식(expression)이 쓰여지는 곳에서 정확하게 데이터를 출력한다.

### 예제
~~~html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
    <p>My first expression: {{ 5 + 5 }}</p>
</div>

</body>
</html>
~~~

 - AngularJS 표현식은 ng-bind 지시문과 동일한 방식으로 AngularJS 데이터를 HTML에 바인딩 한다.

### 예제
~~~html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
    <p>Name: <input type="text" ng-model="name"></p>
    <p>{{name}}</p>
</div>

</body>
</html>
~~~


## [AngularJS Applications]
 - AngularJS modules은 AngularJS applications을 정의한다.
 - AngularJS controllers은 AngularJS applications을 제어한다.
 - 'ng-app' 지시어는 application을 정의, 'ng-controller' 지시어는 controller를 정의

### 예제
~~~html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<p>Try to change the names.</p>

<div ng-app="myApp" ng-controller="myCtrl">

First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{firstName + " " + lastName}}

</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.firstName= "John";
    $scope.lastName= "Doe";
});
</script>

</body>
</html>
~~~

## [AngularJS Module]
 - AngularJS module은 application을 정의한다.

~~~javascript
var app = angular.module('myApp', []);
~~~

## [AngularJS Controller]
 - AngularJS controller는 application을 제어한다.
~~~javascript
app.controller('myCtrl', function($scope) {
    $scope.firstName= "John";
    $scope.lastName= "Doe";
});
~~~
