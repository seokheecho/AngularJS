# AngularJS Http
 - AngularJS AJAX - $ http
 - `$http` 는 원격 서버에서 데이터를 읽는 AngularJS Service이다.


## [AngularJS $ http]
 - AngularJS `$http` 서비스는 서버에 요청을 보내고 응답을 반환한다.
 - 서버에 간단한 요청을하고 결과를 헤더에 표시해보자.
 ~~~html
 <div ng-app="myApp" ng-controller="myCtrl">
 <p>Today's welcome message is:</p>
 <h1>{{myWelcome}}</h1>
 </div>
 <script>
 var app = angular.module('myApp', []);
 app.controller('myCtrl', function($scope, $http) {
   $http.get("welcome.htm")
   .then(function(response) {
     $scope.myWelcome = response.data;
   });
 });
 </script>
 ~~~


## [Methods]
 - 위의 예제 `.get`는 `$http` 서비스 메소드를 사용한다.
 - `.get` 메소드는 `$http` 서비스의 바로가기 메소드(shortcut methods)입니다. 몇 가지 바로가기 방법이 있다.

 - `.delete()`
 - `.get()`
 - `.head()`
 - `.jsonp()`
 - `.patch()`
 - `.post()`
 - `.put()`

 - 위 메소드는 모두 `$http` 서비스 호출의 바로가기이다.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Today's welcome message is:</p>
<h1>{{myWelcome}}</h1>
</div>
<p>The $http service requests a page on the server, and the response is set as the value of the "myWelcome" variable.</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http({
    method : "GET",
    url : "welcome.htm"
  }).then(function mySuccess(response) {
      $scope.myWelcome = response.data;
    }, function myError(response) {
      $scope.myWelcome = response.statusText;
  });
});
</script>
~~~
 - 위의 예제는 객체를 인수로 사용하여 `$http` 서비스를 실행한다. 객체는 HTTP 메소드, URL, 성공시 수행 할 작업 및 실패시 수행 할 작업을 지정한다.


## [Properties]
 - 서버로부터의 응답은 다음과 같은 속성을 가진 객체이다.

 -  `.config` 요청(request)를 생성하기 위해서 사용 된 객체(object)
 - `.data` 문자열(string) 또는 객체(object)가 서버의 응답을 전달한다.
 - `.headers` 헤더 정보를 얻기 위해 사용하는 함수.
 - `.status` HTTP status를 정의하는 숫자.
 - `.statusText` HTTP status를 정의하는 문자열.


~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Data : {{content}}</p>
<p>Status : {{statuscode}}</p>
<p>StatusText : {{statustext}}</p>
</div>
<p>The response object has many properties. This example demonstrate the value of the data, status, and statusText properties.</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http.get("welcome.htm")
  .then(function(response) {
      $scope.content = response.data;
      $scope.statuscode = response.status;
      $scope.statustext = response.statusText;            
  });
});
</script>
~~~
 - 오류를 처리하려면 `.then` 메서드에 하나 이상의 함수를 추가해라.

~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<h1>{{content}}</h1>
</div>
<p>The $http service executes different functions on success and failure.</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http.get("wrongfilename.htm")
  .then(function(response) {
      $scope.content = response.data;
  }, function(response) {
      $scope.content = "Something went wrong";
  });
});
</script>
~~~


## [JSON]
 - 응답에서 얻은 데이터는 JSON 형식이어야한다.
 - JSON은 데이터를 전송하는 좋은 방법이며, AngularJS 또는 다른 JavaScript 내에서 사용하기 쉽다.
 - Example: On the server we have a file that returns a JSON object containing 15 customers, all wrapped in array called records.
 - (Click here to take a look at the JSON object.)</br>
 {
  "records": [
    {
      "Name": "Alfreds Futterkiste",
      "City": "Berlin",
      "Country": "Germany"
    }, ...
  ]
}

 ** ng-repeat지시어는 배열을 통해 반복에 적합하다. :
~~~HTML
 <div ng-app="myApp" ng-controller="customersCtrl">
 <ul>
   <li ng-repeat="x in myData">
     {{ x.Name + ', ' + x.Country }}
   </li>
 </ul>
 </div>
 <script>
 var app = angular.module('myApp', []);
 app.controller('customersCtrl', function($scope, $http) {
   $http.get("customers.php").then(function(response) {
     $scope.myData = response.data.records;
   });
 });
 </script>
~~~
 - application 설명 : `$scope` 및 `$http` 객체를 사용하여 컨트롤러를 정의한다.</br>
 (The application defines the customersCtrl controller, with a $scope and $http object.)
 - `$http` 는 외부 데이터를 요청을 위한 XMLHttpRequest 객체(object)이다.</br>
 ($http is an XMLHttpRequest object for requesting external data.)
 - `$http.get()` 는 https://www.w3schools.com/angular/customers.php 에서 JSON 데이터를 읽는다.</br>
 ($http is an XMLHttpRequest object for requesting external data.)
 - 성공하면 컨트롤러 myData는 서버의 JSON 데이터를 사용하여 scope의 속성을 만든다.</br>
 (On success, the controller creates a property, myData, in the scope, with JSON data from the server.)
