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

### 예제
 - 값을 변경하여 아래 입력 상자의 색상을 변경
~~~html
<div ng-app="" ng-init="myCol='lightblue'">
    <input style="background-color:{{myCol}}" ng-model="myCol">
</div>
~~~

## [AngularJS Numbers]
 - AngularJS 숫자는 JavaScript 숫자와 같다.

### 예제
~~~html
<div ng-app="" ng-init="quantity=1;cost=5">
    <p>Total in dollar: {{ quantity * cost }}</p>
</div>
~~~
 - ng-bind 를 사용한 동일한 예제
~~~HTML
<div ng-app="" ng-init="quantity=1;cost=5">
    <p>Total in dollar: <span ng-bind="quantity * cost"></span></p>
</div>
~~~

** Using ng-init is not very common. You will learn a better way to initialize data in the chapter about controllers. <br/>
(데이터 초기화하는 방법 - Controller chapter에서 더 좋은 방법으로 배워보자!)


## [AngularJS Strings]
 - AngularJS 문자열은 JavaScript 문자열과 같다.

### 예제
~~~html
<div ng-app="" ng-init="firstName='John';lastName='Doe'">
    <p>The name is {{ firstName + " " + lastName }}</p>
</div>
~~~
 - ng-bind 를 사용한 동일한 예제
~~~HTML
<div ng-app="" ng-init="firstName='John';lastName='Doe'">
    <p>The name is <span ng-bind="firstName + ' ' + lastName"></span></p>
</div>
~~~


## [AngularJS Objects]
 - AngularJS 객체는 JavaScript 객체와 같다.

### 예제
~~~html
<div ng-app="" ng-init="person={firstName:'John',lastName:'Doe'}">
    <p>The name is {{ person.lastName }}</p>
</div>
~~~
 - ng-bind 를 사용한 동일한 예제
~~~HTML
<div ng-app="" ng-init="person={firstName:'John',lastName:'Doe'}">
    <p>The name is <span ng-bind="person.lastName"></span></p>
</div>
~~~


## [AngularJS Arrays]
 - AngularJS 배열은 JavaScript 배열과 같다.

### 예제
~~~html
<div ng-app="" ng-init="points=[1,15,19,2,40]">
    <p>The third result is {{ points[2] }}</p>
</div>
~~~
 - ng-bind 를 사용한 동일한 예제
~~~HTML
<div ng-app="" ng-init="points=[1,15,19,2,40]">
    <p>The third result is <span ng-bind="points[2]"></span></p>
</div>
~~~


## [AngularJS Expressions vs. JavaScript Expressions]
  JavaScript 표현식처럼 AngularJS 표현식은 리터럴, 연산자 및 변수를 포함 할 수 있다. <br/>
JavaScript 표현식과 달리 AngularJS 표현식은 HTML 내부에 작성 될 수 있다. <br/>
AngularJS 표현식은 조건부, 루프 및 예외를 지원하지 않지만 JavaScript 표현식은 지원한다. <br/>
AngularJS 표현식은 필터를 지원하지만 JavaScript 표현식은 필터를 지원하지 않는다. <br/>
