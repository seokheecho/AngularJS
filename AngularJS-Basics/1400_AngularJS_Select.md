# AngularJS Select
 - AngularJS를 사용하면 배열이나 객체의 항목을 기반으로 드롭 다운 목록을 만들 수 있다.


## [Creating a Select Box Using ng-options]
 - AngularJS의 객체 또는 배열을 기반으로 드롭 다운 목록을 만들려면 다음 `ng-options` 지시문을 사용해야 한다.
 ~~~HTML
 <div ng-app="myApp" ng-controller="myCtrl">
 <select ng-model="selectedName" ng-options="x for x in names">
 </select>
 </div>
 <script>
 var app = angular.module('myApp', []);
 app.controller('myCtrl', function($scope) {
     $scope.names = ["Emil", "Tobias", "Linus"];
 });
 </script>
 <p>This example shows how to fill a dropdown list using the ng-options directive.</p>
~~~


## [ng-options VS ng-repeat]
 - `ng-repeat` 지시문을 사용하여 동일한 드롭 다운 목록을 만들 수도 있다.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<select>
<option ng-repeat="x in names">{{x}}</option>
</select>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.names = ["Emil", "Tobias", "Linus"];
});
</script>
<p>This example shows how to fill a dropdown list using the ng-repeat directive.</p>
~~~

 - `ng-repeat` 지시문은 배열의 각 항목에 대해 HTML 코드 블록을 반복하기 때문에 드롭 다운 목록에 옵션을 만드는 데 사용할 수 있지만, </br>
   `ng-options ` 지시문은 옵션이 있는 드롭 다운 목록 을 작성하는 데 특히 유용하며 최소한 하나의 중요이점을 갖는다. :
- `ng-options`으로 만들어진 드롭 다운은 선택된 값이 객체이지만, </br>
  `ng-repeat`으로 만들어진 드롭 다운은 문자열이다.


## [What Do I Use?]
 - 객체 배열이 있다고 가정하자. :

~~~JavaScript
 $scope.cars = [
   {model : "Ford Mustang", color : "red"},
   {model : "Fiat 500", color : "white"},
   {model : "Volvo XC90", color : "black"}
 ];
~~~
 - `ng-repeat` 지시어는 선택된 값에 대해 제한을 갖는다, 선택된 값은 문자열이어야만 한다. :

 - Excample Using `ng-repeat`:
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Select a car:</p>
<select ng-model="selectedCar">
<option ng-repeat="x in cars" value="{{x.model}}">{{x.model}}</option>
</select>
<h1>You selected: {{selectedCar}}</h1>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.cars = [
        {model : "Ford Mustang", color : "red"},
        {model : "Fiat 500", color : "white"},
        {model : "Volvo XC90", color : "black"}
    ];
});
</script>
<p>When you use the ng-repeat directive to create dropdown lists, the selected value must be a string.</p>
<p>In this example you will have to choose between the color or the model to be your selected value.</p>
~~~

 - `ng-options` 지시문을 사용할 때 선택한 값은 객체가 될 수 있다.

 - Excample Using `ng-options`:
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Select a car:</p>
<select ng-model="selectedCar" ng-options="x.model for x in cars">
    <option value="">-- Select Car --</option>
</select>
<h1>You selected: {{selectedCar.model}}</h1>
<p>Its color is: {{selectedCar.color}}</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.cars = [
        {model : "Ford Mustang", color : "red"},
        {model : "Fiat 500", color : "white"},
        {model : "Volvo XC90", color : "black"}
    ];
});
</script>
<p>When you use the ng-options directive to create dropdown lists, the selected value can be an object.</p>
<p>In this example you can display both the model and the color of the selected element.</p>
~~~

 - 선택한 값이 객체 일 수 있으면 더 많은 정보를 보유 할 수 있으므로 application의 유연성(flexible)이 향상된다.

 - 튜토리얼에서는 `ng-options` 지시어를 사용한다.

** <option value="">-- Select Car --</option> 을 통해 select box 안에 기본 값을 넣어줘서 선택박스 임을 사용자에게 안내!


## [The Data Source as an Object]

 - 이전 예제에서 데이터 소스는 배열(array)이었지만, 객체(object)를 사용할 수도 있다.
 - key - value 쌍이있는 객체(object)가 있다고 가정하자.

~~~JavaScript
 $scope.cars = {
   car01 : "Ford",
   car02 : "Fiat",
   car03 : "Volvo"
 };
~~~
  - `ng-options` 속성 의 표현식은 객체에 대해 약간 다르다.

  - 객체를 데이터 소스로 사용하면 x키를 y 나타내고 값을 나타낸다.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Select a car:</p>
<select ng-model="selectedCar" ng-options="x for (x, y) in cars">
</select>
<h1>You selected: {{selectedCar}}</h1>
</div>
<p>This example demonstrates the use of an object as the data source when creating a dropdown list.</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.cars = {
        car01 : "Ford",
        car02 : "Fiat",
        car03 : "Volvo"
    }
});
</script>
~~~
 - 선택한 값은 항상 key-value로 이뤄진 한 쌍의 값일 것이다.
 - 한 쌍의 key-value 값 또한 객체(object)이다.
 - 선택한 값은 항상 key-value로 이뤄진 한 쌍의 값이며, 선택된 값은 그 때 한번 객체(object)이다. :
(The selected value will still be the value in a key-value pair, only this time it is an object:)

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Select a car:</p>
<select ng-model="selectedCar" ng-options="x for (x, y) in cars">
</select>
<h1>You selected: {{selectedCar.brand}}</h1>
<h2>Model: {{selectedCar.model}}</h2>
<h3>Color: {{selectedCar.color}}</h3>
<p>Note that the selected value represents an object.</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.cars = {
        car01 : {brand : "Ford", model : "Mustang", color : "red"},
        car02 : {brand : "Fiat", model : "500", color : "white"},
        car03 : {brand : "Volvo", model : "XC90", color : "black"}
    }
});
</script>
~~~

 -  key-value로 이뤄진 한 쌍의 값을 위한 드롭 다운 목록의 옵션이 될 필요가 없으며, 값 또는 객체의 속성 값이 될 수 있다. :

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Select a car:</p>
<select ng-model="selectedCar" ng-options="y.brand for (x, y) in cars">
</select>
<h1>You selected: {{selectedCar.brand}}</h1>
<h2>Model: {{selectedCar.model}}</h2>
<h3>Color: {{selectedCar.color}}</h3>
<p>The visible text inside the dropdown list can also be a property of the value object.</p>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.cars = {
        car01 : {brand : "Ford", model : "Mustang", color : "red"},
        car02 : {brand : "Fiat", model : "500", color : "white"},
        car03 : {brand : "Volvo", model : "XC90", color : "black"}
    }
});
</script>
~~~

** select box 원하는 옵션을 선택해서 넣을 수 있다.</br>
** ng-options="x for (x, y) in cars" </br>
** ng-options="y.brand for (x, y) in cars"
