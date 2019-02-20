# [AngularJS Routing]
 - It is time to create a real AngularJS Application!

## [Make a Shopping List]
 - AngularJS 기능 중 일부를 사용하여 항목을 추가하거나 제거 할 수 있는 쇼핑 목록을 만들 수 있다.


## [Application Explained]

### [Step 1. Getting Started:]
 - 먼저 `myShoppingList` application을 호출하여 이름 `myCtrl`을 지정한 컨트롤러를 추가한다.
 - 컨트롤러는 배열 이름 products배열을 현재 $scope 추가한다.
 - HTML에서 `ng-repeat` 지시문을 사용하여 배열의 항목을 사용하여 목록을 표시한다.
 - 지금까지 배열의 항목을 기반으로 HTML 목록을 만들었다.
~~~HTML
<script>
var app = angular.module("myShoppingList", []);
app.controller("myCtrl", function($scope) {
 $scope.products = ["Milk", "Bread", "Cheese"];
});
</script>
<div ng-app="myShoppingList" ng-controller="myCtrl">
 <ul>
   <li ng-repeat="x in products">{{x}}</li>
 </ul>
</div>
~~~

### [Step 2. Adding Items:]
 - HTML에서 텍스트 필드를 추가하고 `ng-model` 지시문을 사용하여 application에 바인딩한다.
 - 컨트롤러에서 이름 `addItem`으로 지정된 함수를 만들고 입력 필드에 `addItem`의 값을 사용하여 `addMe`을 `products`배열에 항목을 추가한다.
 - 버튼을 추가하고 버튼을 클릭 할 때 함수 `addItem`를 실행 하는 `ng-click` 지시문을 지정한다.
 - 이제 쇼핑 목록에 항목을 추가 할 수 있습니다.
~~~HTML
<script>
var app = angular.module("myShoppingList", []);
app.controller("myCtrl", function($scope) {
 $scope.products = ["Milk", "Bread", "Cheese"];
 $scope.addItem = function () {
   $scope.products.push($scope.addMe);
 }
});
</script>

<div ng-app="myShoppingList" ng-controller="myCtrl">
 <ul>
   <li ng-repeat="x in products">{{x}}</li>
 </ul>
 <input ng-model="addMe">
 <button ng-click="addItem()">Add</button>
</div>
~~~

### [Step 3. Removing Items:]
 - 쇼핑 목록에서 항목을 삭제할 수도 있다.
 - 컨트롤러에서 제거 할 항목의 인덱스를 매개 변수로 사용하는 명명 된 함수 `removeItem`를 만든다.
 - HTML에서 `<span>`각 항목에 대한 요소를 만들고, 현재 `$index`를 가진 함수 `removeItem`를 호출 하는 `ng-click`지시문을 제공해라.
 - 이제 쇼핑 목록에서 항목을 삭제할 수 있습니다.
~~~HTML
<script>
var app = angular.module("myShoppingList", []);
app.controller("myCtrl", function($scope) {
 $scope.products = ["Milk", "Bread", "Cheese"];
 $scope.addItem = function () {
   $scope.products.push($scope.addMe);
 }
 $scope.removeItem = function (x) {
   $scope.products.splice(x, 1);
 }
});
</script>

<div ng-app="myShoppingList" ng-controller="myCtrl">
 <ul>
   <li ng-repeat="x in products">
     {{x}}<span ng-click="removeItem($index)">&times;</span>
   </li>
 </ul>
 <input ng-model="addMe">
 <button ng-click="addItem()">Add</button>
</div>
~~~

### [Step 4. Error Handling:]
 - application에 몇 가지 오류가 있다. 동일한 항목을 두 번 추가하려고하면 application이 충돌합니다. 또한 빈 항목을 추가 할 수 없다.
 - 새 항목을 추가하기 전에 값을 확인하여 해결할 것이다.
 - HTML에서 오류 메시지 용 컨테이너를 추가하고 누군가 기존 항목을 추가하려고하면 오류 메시지를 작성한다.
 - 오류 메시지를 쓸 수있는 쇼핑 목록 :

~~~HTML
<script>
var app = angular.module("myShoppingList", []);
app.controller("myCtrl", function($scope) {
 $scope.products = ["Milk", "Bread", "Cheese"];
 $scope.addItem = function () {
   $scope.errortext = "";
   if (!$scope.addMe) {return;}
   if ($scope.products.indexOf($scope.addMe) == -1) {
     $scope.products.push($scope.addMe);
   } else {
     $scope.errortext = "The item is already in your shopping list.";
   }
 }
 $scope.removeItem = function (x) {
   $scope.errortext = "";
   $scope.products.splice(x, 1);
 }
});
</script>

<div ng-app="myShoppingList" ng-controller="myCtrl">
 <ul>
   <li ng-repeat="x in products">
     {{x}}<span ng-click="removeItem($index)">&times;</span>
   </li>
 </ul>
 <input ng-model="addMe">
 <button ng-click="addItem()">Add</button>
 <p>{{errortext}}</p>
</div>
~~~

### [Step 5. Design:]
 - application은 작동하지만 더 나은 디자인을 사용할 수 있다. W3.CSS 스타일 시트를 사용하여 응용 프로그램의 스타일을 지정한다.
 - W3.CSS 스타일 시트를 추가하고 적절한 클래스를 application에 포함하면 결과는 이 페이지의 맨 위에있는 쇼핑 목록과 동일하다.
 - W3.CSS 스타일 시트를 사용하여 응용 프로그램의 스타일을 지정하자.
~~~HTML
 <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
~~~
