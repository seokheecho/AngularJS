# [AngularJS Includes]
 - AngularJS를 사용하면 외부 파일의 HTML을 포함 할 수 있다.
 - AngularJS를 사용하면 `ng-include` 지시문을 사용하여 HTML 내용을 포함 할 수 있다.
~~~HTML
<body ng-app="">
<div ng-include="'myFile.htm'"></div>
</body>
~~~

## [Include AngularJS Code]
 - `ng-include` 지시어에 포함 된 HTML 파일에는 AngularJS 코드도 포함될 수 있다.
 - myTable.htm 파일 :
~~~HTML
<table>
  <tr ng-repeat="x in names">
    <td>{{ x.Name }}</td>
    <td>{{ x.Country }}</td>
  </tr>
</table>
~~~

 - 웹 페이지에 "myTable.htm"파일을 포함하면 포함 된 파일 안의 코드도 포함하여 모든 AngularJS 코드가 실행된다.

~~~HTML
<body>
<div ng-app="myApp" ng-controller="customersCtrl">
  <div ng-include="'myTable.htm'"></div>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('customersCtrl', function($scope, $http) {
    $http.get("customers.php").then(function (response) {
        $scope.names = response.data.records;
    });
});
</script>
<p>The HTML, and AngularJS code, for this table are located in the file "myTable.htm".</p>
</body>
~~~


## [Include Cross Domains]
 - 기본적으로 `ng-include` 지정문은 다른 도메인의 파일을 포함하도록 허용하지 않는다.

 - 다른 도메인의 파일을 포함시키려면 application의 구성(config) 기능에 법적 파일 및 / 또는 도메인의 화이트리스트를 추가해라.
~~~HTML
<body ng-app="myApp">
<div ng-include="'https://tryit.w3schools.com/angular_include.php'"></div>
<script>
var app = angular.module('myApp', [])
app.config(function($sceDelegateProvider) {
  $sceDelegateProvider.resourceUrlWhitelist([
    'https://tryit.w3schools.com/**'
  ]);
});
</script>
</body>
~~~
** 대상의 서버가 도메인 간 파일 액세스를 허용하는지 확인해라.
