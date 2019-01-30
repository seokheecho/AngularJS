# AngularJS Directives
 - AngularJS를 사용하면 Directives 라는 새로운 속성으로 HTML을 확장 할 수 있다.
 - AngularJS에는 application에 기능을 추가하는 데 사용할 수있는 내장 지시어(Directive) 세트가 있다.
 - AngularJS는 또한 자신의 지시어를 정의 할 수 있게 해준다.


## [AngularJS Directives]
 - AngularJS 지시문은 접두사 `ng-`가 있는 확장 HTML 속성이다.
 - `ng-app` 지시문 AngularJS application을 초기화한다.
 - `ng-init` 지시문은 application 데이터를 초기화한다.
 - `ng-model` 지시문은 HTML controls(input, select, textarea)의 값을 application 데이터에 바인딩한다.
 - 자세한 내용은 AngularJS 지시어(Directive)를 참조 <br/>
  참조 : https://www.w3schools.com/angular/angular_ref_directives.asp

~~~HTML
<div ng-app="" ng-init="firstName='John'">
<p>Name: <input type="text" ng-model="firstName"></p>
<p>You wrote: {{ firstName }}</p>
</div>
~~~
 - `ng-app` 지시문은 또한 AngularJS에게 `<div>` 요소가 AngularJS application의 "owner" 임을 알린다.

## [Data Binding]
 - 위 예제에서의 {{ firstName }} 표현식은 AngularJS data를 바인딩한 표현식이다.
 - AngularJS의 데이터 바인딩은 AngularJS 표현식을 AngularJS 데이터와 바인딩한다.
 - {{ firstName }}에 묶여있다 ng-model="firstName".
 - 다음 예제에서는 두 개의 text fields가 두 개의 ng-model 지시문(directives)과 함께 바인딩된다.

~~~HTML
<div ng-app="" ng-init="quantity=1;price=5">
Quantity: <input type="number" ng-model="quantity">
Costs:    <input type="number" ng-model="price">
Total in dollar: {{ quantity * price }}
</div>
~~~
** Using ng-init is not very common. You will learn a better way to initialize data in the chapter about controllers. <br/>
(데이터 초기화하는 방법 - Controller chapter에서 더 좋은 방법으로 배워보자!)


## [HTML 요소 반복하기]
 - `ng-repeat` 지시문은 HTML 요소를 반복한다.

~~~HTML
<div ng-app="" ng-init="names=['Jani','Hege','Kai']">
  <ul>
    <li ng-repeat="x in names">
      {{ x }}
    </li>
  </ul>
</div>
~~~

 - `ng-repeat` 지시어는 실제로 HTML 요소를 복제한다. 콜렉션의 각 항목에 대해 한 번.

 - `ng-repeat` 오브젝트의 배열에 사용 지시문 :

 ~~~HTML
 <div ng-app="" ng-init="names=[
 {name:'Jani',country:'Norway'},
 {name:'Hege',country:'Sweden'},
 {name:'Kai',country:'Denmark'}]">

 <ul>
   <li ng-repeat="x in names">
     {{ x.name + ', ' + x.country }}
   </li>
 </ul>

 </div>
 ~~~

** AngularJS는 데이터베이스 CRUD (Create Read Update Delete) 애플리케이션에 이상적이다.
이 객체가 데이터베이스의 레코드인지 여부를 생각해보라!


## [ng-app Directive]
 - `ng-app` 지시문은 AngularJS Application의 루트 요소(root elment)를 정의한다.
 - `ng-app` 지시문은 웹 페이지가 로드될 때 Application을 자동으로 초기화 할 것이다. auto-bootstrap(automatically initialize)

## [ng-init Directive]
 - `ng-init` 지시문은 AngularJS 응용 프로그램의 초기 값을 정의한다.
 - 일반적으로 ng-init은 사용하지 않는다. 대신 컨트롤러 또는 모듈을 사용한다.
 - 나중에 컨트롤러와 모듈에 대해 더 배우게된다.

## [ng-model Directive]
 - `ng-model`지시문은 HTML 컨트롤 (input, select, textarea)의 값을 응용 프로그램 데이터에 바인딩한다.
 - `ng-model`지시문은 다음을 수행 할 수도 있다.
     ** 응용 프로그램 데이터 (숫자, 전자 메일, 필수)에 대한 유형 유효성 검사를 제공한다. <br/>
     (Provide type validation for application data (number, email, required).) <br/>
     ** 응용 프로그램 데이터에 대한 상태를 제공한다. (invalid, dirty, touched, error). <br/>
     (Provide status for application data (invalid, dirty, touched, error).) <br/>
     ** HTML 요소에 CSS 클래스를 제공한다. <br/>
     (Provide CSS classes for HTML elements.) <br/>
     ** HTML 요소를 HTML 양식에 바인딩한다. <br/>
     (Bind HTML elements to HTML forms.) <br/>
 - 다음 chapter AngularJS Model에서 `ng-model`에 대해 더 자세히 배워보자!

## [Create New Directives]
 - 내장 된 모든 AngularJS Directive 추가하여 사용자 고유의 Directive를 만들 수 있다. <br/>
   (you can create your own directives.) <br/>
 - `.directive` 함수를 사용하여 새로운 Directive를 만든다.
 - new Directive를 호출하려면 new Directive과 동일한 태그 이름으로 HTML 요소를 만든다.
 - Directive의 이름을 지정할 때는 카멜(낙타)표기법(camel case name - ex) w3TestDirective) 사용해야 하지만, 호출 할 때는 하이픈('-')으로 분리 된 이름(ex) w3-test-directive)을 사용해야한다.

~~~html
<body ng-app="myApp">
<w3-test-directive></w3-test-directive>
<script>
var app = angular.module("myApp", []);
app.directive("w3TestDirective", function() {
  return {
    template : "<h1>Made by a directive!</h1>"
  };
});
</script>
</body>
~~~

 - 다음을 사용하여 지시문(directive)을 호출 할 수 있다. <br/>
 (Element name, Attribute, Class, Comment) <br/>
 - 아래 예제는 모두 동일한 결과를 나타낸다. <br/>

 - Element name
~~~html
 <w3-test-directive></w3-test-directive>
~~~
 - Attribute
~~~html
 <div w3-test-directive></div>
~~~
 - Class
~~~html
 <div class="w3-test-directive"></div>
~~~
 - Comment
~~~html
 <!-- directive: w3-test-directive -->
~~~
** (주석 속성 설정 추가시 가능 - 참고 : https://www.w3schools.com/angular/tryit.asp?filename=try_ng_directive_comment)

## [Restrictions]
 - 일부 메소드에서만 Directive를 호출하도록 제한 할 수 있다.

~~~HTML
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body ng-app="myApp">
<w3-test-directive></w3-test-directive>
<div w3-test-directive></div>
<script>
var app = angular.module("myApp", []);
app.directive("w3TestDirective", function() {
    return {
        restrict : "A",
        template : "<h1>Made by a directive!</h1>"
    };
});
</script>
<p><strong>Note:</strong> By setting the <strong>restrict</strong> property to "A", only the HTML element with the "w3-test-directive" attribute has invoked the directive.</p>
</body>
</html>
~~~

 - 규칙 - 제한 값은 다음과 같다.
    ** E for Element name
    ** A for Attribute
    ** C for Class
    ** M for Comment
 - 기본 default EA 값으로써 요소 이름(Element name)과 속성 이름(Attribute) 모두가 지시문을 호출 할 수 있음을 의미합니다.
