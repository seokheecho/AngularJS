# [AngularJS Animations]
 - AngularJS는 CSS의 도움으로 애니메이션 전환을 제공한다.

## [What is an Animation?]
 - An animation is when the transformation of an HTML element gives you an illusion of motion.
 - Check the checkbox to hide the DIV:
~~~HTML
<style>
div {
  transition: all linear 0.5s;
  background-color: lightblue;
  height: 100px;
  width: 100%;
  position: relative;
  top: 0;
  left: 0;
}
.ng-hide {
  height: 0;
  width: 0;
  background-color: transparent;
  top:-200px;
  left: 200px;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-animate.js"></script>
<body ng-app="ngAnimate">
<h1>Hide the DIV: <input type="checkbox" ng-model="myCheck"></h1>
<div ng-hide="myCheck"></div>
</body>
~~~

 ** Application을 애니메이션으로 채우지 않아야 하지만 일부 애니메이션은 application을 더 쉽게 이해할 수 있게한다.

## [What do I Need?]
 - application에서 애니메이션을 준비하려면 AngularJS Animate 라이브러리를 포함해야한다.

~~~HTML
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-animate.js"></script>
~~~
 - 그런 다음 ngAnimate application의 모듈을 참조해야한다.
~~~HTML
<body ng-app="ngAnimate">
~~~
 - 또는 application에 이름 ngAnimate이 있으면 application 모듈에 종속성(dependency)으로 추가한다.
~~~HTML
<body ng-app="myApp">
<h1>Hide the DIV: <input type="checkbox" ng-model="myCheck"></h1>
<div ng-hide="myCheck"></div>
<script>
var app = angular.module('myApp', ['ngAnimate']);
</script>
~~~


## [What Does ngAnimate Do?]
 - ngAnimate 모듈은 클래스를 추가하고 제거한다.
 - ngAnimate 모듈은 HTML 요소를 애니메이션화 하지 않지만, ngAnimate가 HTML 요소의 숨기기 또는 표시와 같은 특정 이벤트를 감지하면, 요소는 미리 정의 된 클래스를 가져 와서 애니메이션을 만들 수 있다.
 - AngularJS의 클래스 추가/제거 지시문은 다음과 같다.

  - `ng-show`
  - `ng-hide`
  - `ng-class`
  - `ng-view`
  - `ng-include`
  - `ng-repeat`
  - `ng-if`
  - `ng-switch`

 - `ng-show` 및 `ng-hide` 지침은 추가하거나 제거 `ng-hide`클래스 값이다.
 - 다른 지시문 `ng-enter`은 DOM에 입력 할 때 클래스 값을 추가 하고 DOM에서 `ng-leave` 제거되면 속성을 추가한다.
 - `ng-repeat` 지침도 추가 `ng-move` HTML 요소의 위치가 변경 될 때 클래스 값이다.
 - 또한 애니메이션 중에 HTML 요소에는 애니메이션이 끝나면 제거되는 클래스 값 집합이 있다. 예 : `ng-hide`지시문은 다음 클래스 값을 추가한다.

 - `ng-animate`
 - `ng-hide-animate`
 - `ng-hide-add` (요소가 숨겨져있는 경우)
 - `ng-hide-remove` (요소가 표시 될 경우)
 - `ng-hide-add-active` (요소가 숨겨져있는 경우)
 - `ng-hide-remove-active` (요소가 표시 될 경우)


## [Animations Using CSS]
 - CSS 전환 또는 CSS 애니메이션을 사용하여 HTML 요소를 애니메이션으로 만들 수 있다. 이 자습서에서는 두 가지를 모두 보여준다.
 - CSS 애니메이션에 대한 자세한 내용은 CSS 전환 자습서 와 CSS 애니메이션 자습서를 참조하자.
 - CSS Transition Tutorial : (https://www.w3schools.com/css/css3_transitions.asp)
 - CSS Animation Tutorial : (https://www.w3schools.com/css/css3_animations.asp)


## [CSS Transitions]
 - CSS 전환을 사용하면 주어진 기간 동안 CSS 속성 값을 한 값에서 다른 값으로 부드럽게 변경할 수 있다.
 - DIV 요소가 .`ng-hide`클래스를 가져오면 전환에는 0.5 초가 걸리고 높이는 100px에서 0으로 부드럽게 변경된다.

~~~HTML
<style>
div {
  transition: all linear 0.5s;
  background-color: lightblue;
  height: 100px;
}
.ng-hide {
  height: 0;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-animate.js"></script>
<body ng-app="myApp">
<h1>Hide the DIV: <input type="checkbox" ng-model="myCheck"></h1>
<div ng-hide="myCheck"></div>
<script>
var app = angular.module('myApp', ['ngAnimate']);
</script>
</body>
~~~


## [CSS Animations]
 - CSS 애니메이션을 사용하면 CSS 속성 값을 일정 기간 동안 한 값에서 다른 값으로 부드럽게 변경할 수 있다.
 - DIV 요소가 `.ng-hide`클래스를 가져오면 myChange 애니메이션이 실행되어 100px에서 0으로 부드럽게 높이가 변경된다.

~~~HTML
<style>
@keyframes myChange {
  from {
      height: 100px;
  } to {
      height: 0;
  }
}
div {
  height: 100px;
  background-color: lightblue;
}
div.ng-hide {
  animation: 0.5s myChange;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-animate.js"></script>
<body ng-app="ngAnimate">
Hide the DIV: <input type="checkbox" ng-model="myCheck">
<div ng-hide="myCheck">
</div>
</body>
~~~
