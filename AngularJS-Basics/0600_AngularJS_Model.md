# AngularJS Model
 - `ng-model` 지시문(directive)은 HTML 컨트롤(input, select, textarea)의 값을 application data에 바인딩한다.


## [ng-model Directive]
 - `ng-model` 지시문을 사용하면 입력 필드의 값을 AngularJS로 만든 변수에 바인딩 할 수 있다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
  Name: <input ng-model="name">
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.name = "John Doe";
});
</script>
~~~


## [Two-Way Binding]
 - 바인딩은 두 가지 방식으로 진행된다. 사용자가 입력 필드 안의 값을 변경하면 AngularJS 속성도 값을 변경한다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
Name: <input ng-model="name">
<h1>You entered: {{name}}</h1>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.name = "John Doe";
});
</script>
~~~


## [사용자 입력 유효성 검사(Validate User Input)]
 - `ng-model` 지시자는 application data(number, e-mail, required)에 대한 입력 유효성 검사를 제공할 수 있다.

~~~HTML
<form ng-app="" name="myForm">
    Email:
    <input type="email" name="myAddress" ng-model="text">
    <span ng-show="myForm.myAddress.$error.email">Not a valid e-mail address</span>
</form>
~~~

 - 위의 예에서 `ng-show` 속성 의 표현식이 true로 return 될 경우에만 `<span>...</span>` 내용이 표시된다.
 - 속성의 `ng-model` 속성이 존재하지 않으면 AngularJS가 속성을 만든다.


## [Application Status]
 - `ng-model` 지시문은 application data(valid, dirty, touched, error)에 대한 상태를 제공 할 수 있다.

~~~HTML
<form ng-app="" name="myForm" ng-init="myText = 'post@myweb.com'">
Email:
<input type="email" name="myAddress" ng-model="myText" required>
<p>Edit the e-mail address, and try to change the status.</p>
<h1>Status</h1>
<p>Valid: {{myForm.myAddress.$valid}} (if true, the value meets all criteria).</p>
<p>Dirty: {{myForm.myAddress.$dirty}} (if true, the value has been changed).</p>
<p>Touched: {{myForm.myAddress.$touched}} (if true, the field has been in focus).</p>
</form>
~~~


## [CSS Classes]
 - `ng-model` 지시어는 자신의 상태에 따라, HTML 요소에 CSS 클래스를 제공한다. :

 ~~~HTML
 <style>
input.ng-invalid {
  background-color: lightblue;
}
</style>
<body>
<form ng-app="" name="myForm">
  Enter your name:
  <input name="myName" ng-model="myText" required>
</form>
<p>Edit the text field and it will get/lose classes according to the status.</p>
<p><b>Note:</b> A text field with the "required" attribute is not valid when it is empty.</p>
 ~~~

 - `ng-model` 지시어는 지정 폼 필드의 상태에 따라, 다음 클래스 삭제/추가 한다. :

 **ng-empty
 **ng-not-empty
 **ng-touched
 **ng-valid
 **ng-untouched
 **ng-invalid
 **ng-dirty
 **ng-pending
 **ng-pristine
