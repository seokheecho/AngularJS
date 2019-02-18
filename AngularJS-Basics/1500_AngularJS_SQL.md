# AngularJS SQL
 - AngularJS는 데이터베이스의 데이터를 표시하는 데 적합하다. 데이터가 JSON 형식인지 확인하자!

## [Fetching Data From a PHP Server Running MySQL]
 - MySQL을 실행하는 PHP 서버에서 데이터 가져 오기
~~~HTML
 <div ng-app="myApp" ng-controller="customersCtrl">
 <table>
   <tr ng-repeat="x in names">
     <td>{{ x.Name }}</td>
     <td>{{ x.Country }}</td>
   </tr>
 </table>
 </div>
 <script>
 var app = angular.module('myApp', []);
 app.controller('customersCtrl', function($scope, $http) {
   $http.get("customers_mysql.php")
   .then(function (response) {$scope.names = response.data.records;});
 });
 </script>
~~~

## [Fetching Data From an ASP.NET Server Running SQL]
~~~HTML
 <div ng-app="myApp" ng-controller="customersCtrl">
 <table>
   <tr ng-repeat="x in names">
     <td>{{ x.Name }}</td>
     <td>{{ x.Country }}</td>
   </tr>
 </table>
 </div>
 <script>
 var app = angular.module('myApp', []);
 app.controller('customersCtrl', function($scope, $http) {
   $http.get("customers_sql.aspx")
   .then(function (response) {$scope.names = response.data.records;});
 });
 </script>
 ~~~


## [Server Code Examples]
 - 다음 섹션은 SQL 데이터를 가져 오는 데 사용되는 서버 코드 목록이다.
 - 1) PHP와 MySQL 사용하기. JSON 반환.
 - 2) PHP와 MS Access 사용하기. JSON 반환.
 - 3) ASP.NET, VB 및 MS Access 사용. JSON 반환.
 - 4) ASP.NET, Razor 및 SQL Lite 사용. JSON 반환.


## [Cross-Site HTTP Requests]
 - 요청하는 페이지가 아닌 다른 서버의 데이터 요청은 사이트 간 HTTP 요청 이라고 한다.
 - 교차 사이트 요청은 웹에서 자주 발생한다. 많은 페이지가 다른 서버의 CSS, 이미지 및 스크립트를로드한다.
 - 최신 브라우저에서는 보안상의 이유로 스크립트의 사이트 간 HTTP 요청이 동일한 사이트 로 제한된다.

 - 다음 예제는 PHP 예제에서 사이트 간 액세스를 허용하기 위해 추가되었다.

 `header("Access-Control-Allow-Origin: *");` </br>

 1. 서버 코드 PHP와 MySQL
 2. 서버 코드 PHP 및 MS 액세스
 3. 서버 코드 ASP.NET, VB 및 MS 액세스
 4. 서버 코드 ASP.NET, Razor C # 및 SQL Lite

 - 예제 참고 : https://www.w3schools.com/angular/angular_sql.asp
