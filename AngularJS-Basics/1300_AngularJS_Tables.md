# AngularJS Tables
 - `ng-repeat` 지시문은 테이블을 표시하는 데 적합하다.


## [Displaying Data in a Table]
 - AngularJS를 사용하여 표를 표시하는 것은 매우 간단하다.
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
  $http.get("customers.php")
  .then(function (response) {
      $scope.names = response.data.records;
  });
});
</script>
~~~


## [Displaying with CSS Style]
 - 멋지게 만들려면 페이지에 CSS를 추가하자.
 - CSS 스타일
 ~~~HTML
 <style>
 table, th , td  {
   border: 1px solid grey;
   border-collapse: collapse;
   padding: 5px;
 }
 table tr:nth-child(odd) {
   background-color: #f1f1f1;
 }
 table tr:nth-child(even) {
   background-color: #ffffff;
 }
 </style>
 <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
 <body>
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
     $http.get("customers.php")
     .then(function (response) {$scope.names = response.data.records;});
 });
 </script>
 </body>
~~~


## [Display with orderBy Filter]
 - 표를 정렬하려면 orderBy 필터를 추가하자.
~~~HTML
<table>
  <tr ng-repeat="x in names | orderBy : 'Country'">
    <td>{{ x.Name }}</td>
    <td>{{ x.Country }}</td>
  </tr>
</table>
~~~


## [Display with uppercase Filter]
 - 대문자를 표시하려면 대문자 필터를 추가하자.
~~~HTML
<table>
  <tr ng-repeat="x in names">
    <td>{{ x.Name }}</td>
    <td>{{ x.Country | uppercase }}</td>
  </tr>
</table>
~~~


## [Display the Table Index ($index)]
 - 테이블 인덱스를 표시하려면 `$index`와 함께 <td>를 추가하자.
~~~HTML
<table>
  <tr ng-repeat="x in names">
    <td>{{ $index + 1 }}</td>
    <td>{{ x.Name }}</td>
    <td>{{ x.Country }}</td>
  </tr>
</table>
~~~


## [Using $even and $odd]

~~~HTML
<table>
  <tr ng-repeat="x in names">
    <td ng-if="$odd" style="background-color:#f1f1f1">{{ x.Name }}</td>
    <td ng-if="$even">{{ x.Name }}</td>
    <td ng-if="$odd" style="background-color:#f1f1f1">{{ x.Country }}</td>
    <td ng-if="$even">{{ x.Country }}</td>
  </tr>
</table>
~~~
