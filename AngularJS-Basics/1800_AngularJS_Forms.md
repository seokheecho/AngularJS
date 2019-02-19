# AngularJS Forms
 - AngularJS의 Forms은 입력 컨트롤의 데이터 바인딩 및 유효성 검사를 제공한다.

## [Input Controls]
 - 입력(Input) Controls은 HTML 입력 요소(input elments)이다. :

 - 입력 요소(input elements)
 - 요소 선택(select elements)
 - 버튼 요소(button elements)
 - 텍스트 영역 요소(textarea elements)


## [Data-Binding]
 - 입력 컨트롤(input controls)은 `ng-model` 지시문을 사용하여 데이터 바인딩을 제공한다.
~~~HTML
<input type="text" ng-model="firstname">
~~~
 - application에 이제 firstname으로 이름 지어진 속성(property)이 있다.
 - 이 `ng-model` 지시문은 input controller를 나머지 application에 바인딩한다.
 - 이 속성(property) firstname은 컨트롤러에서 참조 할 수 있다.
~~~HTML
<div ng-app="myApp" ng-controller="formCtrl">
  <form>
    First Name: <input type="text" ng-model="firstname">
  </form>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('formCtrl', function($scope) {
    $scope.firstname = "John";
});
</script>
~~~
 - 또한 application의 다른 곳에서도 참조 할 수 있다.
~~~HTML
<div ng-app="">
  <form>
    First Name: <input type="text" ng-model="firstname">
  </form>
  <h1>You entered: {{firstname}}</h1>
</div>
<p>Change the name inside the input field, and you will see the name in the header changes accordingly.</p>

~~~


## [Checkbox]
 - 체크 박스에는 true또는 값이 false 있다. `ng-model` 지시문을 확인란에 적용하고 application에서 해당 값을 사용한다.
 - 확인란을 선택하면 머리글 표시 :
~~~HTML
<div ng-app="">
  <form>
    Check to show a header:
    <input type="checkbox" ng-model="myVar">
  </form>
  <h1 ng-show="myVar">My Header</h1>
</div>
<p>The header's ng-show attribute is set to true when the checkbox is checked.</p>
~~~


## [Radiobuttons]
 - `ng-model` 지시문을 사용하여 application에 라디오 버튼을 바인딩한다.
 - 동일한 `ng-model`의 라디오버튼은 다른 값을 가질 수 있지만, 선택한 버튼 하나만 사용된다.
 - 선택한 라디오 버튼의 값에 따라 텍스트를 표시해보자.
~~~HTML
<form>
  Pick a topic:
  <input type="radio" ng-model="myVar" value="dogs">Dogs
  <input type="radio" ng-model="myVar" value="tuts">Tutorials
  <input type="radio" ng-model="myVar" value="cars">Cars
</form>
<div ng-switch="myVar">
  <div ng-switch-when="dogs">
     <h1>Dogs</h1>
     <p>Welcome to a world of dogs.</p>
  </div>
  <div ng-switch-when="tuts">
     <h1>Tutorials</h1>
     <p>Learn from examples.</p>
  </div>
  <div ng-switch-when="cars">
     <h1>Cars</h1>
     <p>Read about cars.</p>
  </div>
</div>
<p>The ng-switch directive hides and shows HTML sections depending on the value of the radio buttons.</p>
~~~
 - myVar의 값은 dogs, tuts 또는 cars 이 될 것이다.


## [Selectbox]
 - `ng-model` 지시문을 사용하여 application의 선택상자(selectbox)를 바인딩한다.
 - 속성(property)에 정의 된 `ng-model` 속성은 selectbox에서 선택한 옵션의 값을 갖는다.
 - 선택한 옵션의 값에 따라 텍스트를 표시해보자.
~~~HTML
<body ng-app="">
<form>
  Select a topic:
  <select ng-model="myVar">
    <option value="">
    <option value="dogs">Dogs
    <option value="tuts">Tutorials
    <option value="cars">Cars
  </select>
</form>
<div ng-switch="myVar">
  <div ng-switch-when="dogs">
     <h1>Dogs</h1>
     <p>Welcome to a world of dogs.</p>
  </div>
  <div ng-switch-when="tuts">
     <h1>Tutorials</h1>
     <p>Learn from examples.</p>
  </div>
  <div ng-switch-when="cars">
     <h1>Cars</h1>
     <p>Read about cars.</p>
  </div>
</div>
<p>The ng-switch directive hides and shows HTML sections depending on the value of the dropdown list.</p>
</body>
~~~
 - myVar의 값은 dogs, tuts 또는 cars 이 될 것이다.


## [An AngularJS Form Example]
 - 예제 참고 : https://www.w3schools.com/angular/angular_forms.asp


## [Application Code]
~~~HTML
<body>
<div ng-app="myApp" ng-controller="formCtrl">
  <form novalidate>
    First Name:<br>
    <input type="text" ng-model="user.firstName"><br>
    Last Name:<br>
    <input type="text" ng-model="user.lastName">
    <br><br>
    <button ng-click="reset()">RESET</button>
  </form>
  <p>form = {{user}}</p>
  <p>master = {{master}}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('formCtrl', function($scope) {
    $scope.master = {firstName:"John", lastName:"Doe"};
    $scope.reset = function() {
        $scope.user = angular.copy($scope.master);
    };
    $scope.reset();
});
</script>
</body>
~~~
 - novalidate 속성(attribute)은 HTML5의 새로운 기능이다. 기본 브라우저 유효성 검사를 비활성화한다.


## [Example Explained]
 - 1) `ng-app` 지시문은 AngularJS와 application을 정의한다.
 - 2) `ng-controller` 지시어는 application controller를 정의한다.
 - 3) `ng-model` 지시자는 두개의 입력 요소를 모델 안의 사용자(user) 객체로 바인딩한다.
 - 4) formCtrl 컨트롤러는 초기 값을 마스터(master) 객체로 세팅한다. 그리고 `reset()` 함수(method)를 정의한다.
 - 5) `reset()` 메소드은 user 객체를 master 객체로 동일하게 하는 설정이다.
 - 6) `ng-click` 지시문은 `reset()` 버튼을 클릭 할 경우에만 호출된다.
 - 7) `novalidate` 속성은 이 application에는 필요하지 않지만, 일반적으로 표준 HTML5 유효성 검사를 재정의하기 위해 AngularJS 양식에서 사용한다.
