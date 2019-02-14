# AngularJS Services
 - AngularJS에서는 자신만의 서비스(service)를 만들거나 많은 기본 제공 서비스(built-in services) 중 하나를 사용할 수 있다.


## [What is a Service?]
 - AngularJS에서 서비스(Service)는 AngularJS application에서만 사용할 수 있는 함수(function) 또는 객체(object)이다.
 - AngularJS에서는 약 30개의 내장 서비스(built-in services)가 있다. 그 중 하나가 `$location` 서비스이다.
 - 이 `$location` 서비스에는 현재 웹 페이지의 위치에 대한 정보를 반화하는 메서드가 있다.</br>

 - `$location` 컨트롤러 에서 서비스 사용 :
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>The url of this page is:</p>
<h3>{{myUrl}}</h3>
</div>
<p>This example uses the built-in $location service to get the absolute url of the page.</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $location) {
    $scope.myUrl = $location.absUrl();
});
</script>
~~~
 - 유의하라! `$location` 서비스(Service)가 인수(argument)로 컨트롤러(Controller)에 전달된다.
 - 컨트롤러(Controller)에서 서비스(Service)를 사용하려면 종속성(dependency)으로 정의해야한다.


## [Why use Services?]
 - `$location`서비스와 같이 많은 서비스의 경우 객체처럼 이미 DOM에 있는 객체를 사용할 수있는 것처럼 보이지만 `window.location` 적어도 AngularJS application에는 몇 가지 제한 사항이 있다.

 - AngularJS는 지속적으로 application을 관리하며, 변경 및 이벤트를 올바르게 처리하기 위해 AngularJS는 `window.location` 객체를 사용하는 대신에 `$location` 서비스르 사용하는 것을 선호한다.


## [The $http Service]
 - `$http` 서비스는 AngularJS application에서 가장 일반적으로 사용되는 서비스 중 하나입니다. 이 서비스는 서버에 요청을 보내고 application이 응답을 처리하도록한다.
 - `$http` 서비스를 사용하여 서버에서 데이터를 요청해보자.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Today's welcome message is:</p>
<h1>{{myWelcome}}</h1>
</div>
<p>The $http service requests a page on the server, and the response is set as the value of the "myWelcome" variable.
</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http.get("welcome.htm").then(function (response) {
      $scope.myWelcome = response.data;
  });
});
</script>
~~~
 - 이 예제는 `$http` 서비스 의 매우 간단한 사용을 보여준다.
 - AngularJS Http 튜토리얼 `$http` 에서 서비스에 대해 자세히 알아보자.
 (https://www.w3schools.com/angular/angular_http.asp)


## [The $timeout Service]
 - `$timeout` 서비스는 AngularJS 버전의 `window.setTimeout` 기능이다.
 -  2 초 후에 새 메시지 표시 :
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>This header will change after two seconds:</p>
<h1>{{myHeader}}</h1>
</div>
<p>The $timeout service runs a function after a specified number of milliseconds.</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $timeout) {
  $scope.myHeader = "Hello World!";
  $timeout(function () {
      $scope.myHeader = "How are you today?";
  }, 2000);
});
</script>
~~~


## [The $interval Service]
 - `$interval` 서비스는 AngularJS 버전의 `window.setInterval` 기능이다.
 - 매초마다 시간 표시 :
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>The time is:</p>
<h1>{{theTime}}</h1>
</div>
<p>The $interval service runs a function every specified millisecond.</p>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $interval) {
  $scope.theTime = new Date().toLocaleTimeString();
  $interval(function () {
      $scope.theTime = new Date().toLocaleTimeString();
  }, 1000);
});
</script>
~~~


## [Create Your Own Service]
 - 자체 서비스를 만들려면 서비스를 모듈에 연결하자.
 - 다음과 같은 서비스를 만듭니다 hexafy :
~~~JavaScript
 app.service('hexafy', function() {
   this.myFunc = function (x) {
     return x.toString(16);
   }
 });
~~~
 - 사용자 정의 된 서비스를 사용하려면 컨트롤러 정의시 종속성(dependency)으로 추가해라.
 - `hexafy` 을 16 진수로 변환하려면 이전 hexafy 명으로 만든 사용자 지정 서비스(custom made service)를 사용해라.

~~~JavaScript
 app.controller('myCtrl', function($scope, hexafy) {
   $scope.hex = hexafy.myFunc(255);
 });
 ~~~


## [Use a Custom Service Inside a Filter]
 - 일단 서비스를 생성하고 application에 연결하면 컨트롤러, 지시문, 필터 또는 다른 서비스 내부에서 서비스를 사용할 수 있다.
(Once you have created a service, and connected it to your application, you can use the service in any controller, directive, filter, or even inside other services.)
- 필터 내에서 서비스를 사용하려면 필터를 정의 할 때 서비스를 종속(dependency) 항목으로 추가해라.
- hexafy필터에 사용 된 서비스 myFormat:

~~~HTML
<div ng-app="myApp">
Convert the number 255, using a custom made service inside a custom made filter:
<h1>{{255 | myFormat}}</h1>
</div>
<script>
var app = angular.module('myApp', []);
app.service('hexafy', function() {
    this.myFunc = function (x) {
        return x.toString(16);
    }
});
app.filter('myFormat',['hexafy', function(hexafy) {
    return function(x) {
        return hexafy.myFunc(x);
    };
}]);
</script>
~~~

 - 객체 또는 배열의 값을 표시 할 때 필터를 사용할 수 있다.
 - 다음과 같은 서비스를 만듭니다 hexafy.
~~~HTML
<div ng-app="myApp" ng-controller="myCtrl">
<p>Use a filter when displaying the array [255, 251, 200]:</p>
<ul>
  <li ng-repeat="x in counts">{{x | myFormat}}</li>
</ul>
<p>This filter uses a service that converts numbers into hexadecimal values.</p>
</div>
<script>
var app = angular.module('myApp', []);
app.service('hexafy', function() {
    this.myFunc = function (x) {
        return x.toString(16);
    }
});
app.filter('myFormat',['hexafy', function(hexafy) {
    return function(x) {
        return hexafy.myFunc(x);
    };
}]);
app.controller('myCtrl', function($scope) {
    $scope.counts = [255, 251, 200];
});
</script>
~~~
** controller - filter - service
