# AngularJS Events
 - AngularJS에는 자체 HTML 이벤트 지시문이 있다.

## [AngularJS Events]
 - 다음 지시문 중 하나 이상을 사용하여 HTML 요소에 AngularJS 이벤트 리스너를 추가 할 수 있다.

- `ng-blur`
- `ng-change`
- `ng-click`
- `ng-copy`
- `ng-cut`
- `ng-dblclick`
- `ng-focus`
- `ng-keydown`
- `ng-keypress`
- `ng-keyup`
- `ng-mousedown`
- `ng-mouseenter`
- `ng-mouseleave`
- `ng-mousemove`
- `ng-mouseover`
- `ng-mouseup`
- `ng-paste`

 - 이벤트 지시문을 사용하면 특정 사용자 이벤트에서 AngularJS 함수를 실행할 수 있다.
 - AngularJS 이벤트는 HTML 이벤트를 겹쳐 쓰지 않으므로 두 이벤트가 모두 실행된다.


## [Mouse Events]
 - 마우스 이벤트는 커서가 요소 위로 이동하면 다음 순서로 발생한다.

 - 1) `ng-mouseover`
 - 2)` ng-mouseenter`
 - 3) `ng-mousemove`
 - 4) `ng-mouseleave`

 - 또는 요소에서 마우스 버튼을 클릭하면 다음 순서대로 수행됩니다.

 - `ng-mousedown`
 - `ng-mouseup`
 - `ng-click`

 - 모든 HTML 요소에 마우스 이벤트를 추가 할 수 있다.

 - 마우스가 H1 요소 위로 이동할 때 카운트 변수를 증가시킨다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<h1 ng-mousemove="count = count + 1">Mouse over me!</h1>
<h2>{{ count }}</h2>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.count = 0;
});
</script>
~~~


## [The ng-click Directive]
 - 이 `ng-click` 지시어는 요소가 클릭 될 때 실행될 AngularJS 코드를 정의한다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<button ng-click="count = count + 1">Click me!</button>
<p>{{ count }}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.count = 0;
});
</script>
~~~

 - 함수를 참조 할 수도 있다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<button ng-click="myFunction()">Click me!</button>
<p>{{ count }}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.count = 0;
  $scope.myFunction = function() {
    $scope.count++;
  }
});
</script>
~~~

## [Toggle, True/False]
 - 버튼을 클릭 할 때 HTML 코드 섹션을 표시하고 버튼을 다시 클릭하면 숨지며, 드롭 다운 메뉴처럼 버튼이 토글 스위치처럼 동작하도록 만들어보자.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<button ng-click="myFunc()">Click Me!</button>
<div ng-show="showMe">
    <h1>Menu:</h1>
    <div>Pizza</div>
    <div>Pasta</div>
    <div>Pesce</div>
</div>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.showMe = false;
    $scope.myFunc = function() {
        $scope.showMe = !$scope.showMe;
    }
});
</script>
<p>Click the button to show/hide the menu.</p>
~~~
 - showMe 변수는 거짓값으로 시작 false.
 (The showMe variable starts out as the Boolean value false.)
 - 이 myFunc함수는 `!`(not) 연산자를 showMe사용하여 변수를 그 반대의 값으로 설정한다.
 (The myFunc function sets the showMe variable to the opposite of what it is, by using the ! (not) operator.)


## [$event Object]
 - $event 함수를 호출 할 때 객체를 인수로 전달할 수 있다.
 - $event 객체는 브라우저의 이벤트 객체를 포함한다.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<h1 ng-mousemove="myFunc($event)">Mouse Over Me!</h1>
<p>Coordinates: {{x + ', ' + y}}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
  $scope.myFunc = function(myE) {
    $scope.x = myE.clientX;
    $scope.y = myE.clientY;
  }
});
</script>
~~~
