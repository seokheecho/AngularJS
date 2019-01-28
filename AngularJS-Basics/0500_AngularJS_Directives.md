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
 - `ng-app` 지시문은 또한 AngularJS에게 `<div>` 요소가 AngularJS apapplication의 "owner" 임을 알린다.

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


## [ng-app 지침]
 - `ng-app` 지시문은 AngularJS Application의 루트 요소(root elment)를 정의한다.
 - `ng-app` 지시문은 웹 페이지가 로드될 때 Application을 자동으로 초기화 할 것이다. auto-bootstrap(automatically initialize)

 ## [ng-init 지시문]
  -
  
  
  a
