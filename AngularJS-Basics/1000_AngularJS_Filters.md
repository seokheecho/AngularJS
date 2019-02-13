# AngularJS Filters
 - AngularJS에 필터를 추가하여 데이터 형식을 지정할 수 있다.


## [AngularJS Filters]
 - AngularJS는 데이터를 변환하는 필터를 제공한다. :
 - `currency` 숫자를 통화 형식으로 포맷
 - `date` 날짜를 지정된 형식으로 포맷
 - `filter` 배열에서 항목의 하위 집합을 선택
 - `json` 객체를 JSON 문자열로 포맷
 - `limitTo` 배열/문자열을 지정된 수의 요소/문자로 제한
 - `lowercase` 문자열을 소문자로 포맷
 - `number` 숫자를 문자열로 지정
 - `orderBy` 표현식(expression)으로 배열을 정렬
 - `uppercase` 문자열을 대문자로 포맷


## [Adding Filters to Expressions]
 - 필터는 파이프 문자 `|` 와 필터를 사용하여 표현식에 추가 할 수 있다.

 - uppercase대문자 필터 형식 문자열 :
~~~HTML
<div ng-app="myApp" ng-controller="personCtrl">
<p>The name is {{ lastName | uppercase }}</p>
</div>
 ~~~

 - lowercase소문자 필터 형식 문자열 :
 ~~~HTML
<div ng-app="myApp" ng-controller="personCtrl">
<p>The name is {{ lastName | lowercase }}</p>
</div>
~~~


## [Adding Filters to Directives]
 - 필터는 `ng-repeat `파이프 문자 `|`와 필터를 사용하여 지시문에 추가된다.

 - orderBy필터 배열을 정렬한다 :
~~~HTML
<div ng-app="myApp" ng-controller="namesCtrl">
 <ul>
   <li ng-repeat="x in names | orderBy:'country'">
     {{ x.name + ', ' + x.country }}
   </li>
 </ul>
</div>
~~~


## [The currency Filter]
 - currency필터는 통화로 숫자를 포맷 :

~~~HTML
<div ng-app="myApp" ng-controller="costCtrl">
<h1>Price: {{ price | currency }}</h1>
</div>
~~~

 - AngularJS 통화 필터 목록 에서 통화 필터에 대해 자세히 알아보라.</br>
(https://www.w3schools.com/angular/ng_filter_currency.asp)


## [The filter Filter]
 - filter필터 배열의 서브 세트를 선택한다.
 - filter필터는 배열에서만 사용될 수 있고, 오직 matching items을 포함하는 배열을 반환한다.

 - 문자 "i"가 포함 된 이름을 반환한다.
~~~HTML
<div ng-app="myApp" ng-controller="namesCtrl">
<ul>
  <li ng-repeat="x in names | filter : 'i'">
    {{ x }}
  </li>
</ul>
</div>
~~~

- AngularJS 필터 필터 참조 에서 필터 필터에 대해 자세히 읽어보라.</br>
(https://www.w3schools.com/angular/ng_filter_filter.asp)


## [Filter an Array Based on User Input]
 - `ng-model` 입력 필드에 지시문을 설정하여 입력 필드의 값을 필터의 표현식으로 사용할 수 있다.
 - 입력 필드에 문자를 입력하면 목록에 따라 일치/축소됩니다.</br>
 ** 검색창 ‘컨텍스트 자동완성’ 기능을 생각해보면 이해하기 쉽다.
(https://www.w3schools.com/angular/angular_filters.asp)
~~~HTML
<div ng-app="myApp" ng-controller="namesCtrl">
<p><input type="text" ng-model="test"></p>
<ul>
  <li ng-repeat="x in names | filter : test">
     {{ x }}
  </li>
</ul>
</div>
~~~


## [Sort an Array Based on User Input]
 - 정렬 순서를 변경하려면 테이블 헤더를 클릭해라.
 - `ng-click` 테이블 헤더에 지시문을 추가하여, 배열의 정렬 순서를 변경하는 함수를 실행할 수 있다.

~~~HTML
 <div ng-app="myApp" ng-controller="namesCtrl">
 <table border="1" width="100%">
   <tr>
     <th ng-click="orderByMe('name')">Name</th>
     <th ng-click="orderByMe('country')">Country</th>
   </tr>
   <tr ng-repeat="x in names | orderBy:myOrderBy">
     <td>{{x.name}}</td>
     <td>{{x.country}}</td>
   </tr>
 </table>
 </div>

 <script>
 angular.module('myApp', []).controller('namesCtrl', function($scope) {
   $scope.names = [
     {name:'Jani',country:'Norway'},
     {name:'Carl',country:'Sweden'},
     {name:'Margareth',country:'England'},
     {name:'Hege',country:'Norway'},
     {name:'Joe',country:'Denmark'},
     {name:'Gustav',country:'Sweden'},
     {name:'Birgit',country:'Denmark'},
     {name:'Mary',country:'England'},
     {name:'Kai',country:'Norway'}
   ];
   $scope.orderByMe = function(x) {
     $scope.myOrderBy = x;
   }
 });
 </script>
~~~


## [Custom Filters]
 - 모듈에 새 필터 팩토리 함수를 등록하여 고유한 필터를 만들 수 있다.
 - "myFormat"이라는 사용자 정의 필터를 만든다.
~~~HTML
 <ul ng-app="myApp" ng-controller="namesCtrl">
   <li ng-repeat="x in names">
     {{x | myFormat}}
   </li>
 </ul>

 <script>
 var app = angular.module('myApp', []);
 app.filter('myFormat', function() {
   return function(x) {
     var i, c, txt = "";
     for (i = 0; i < x.length; i++) {
       c = x[i];
       if (i % 2 == 0) {
         c = c.toUpperCase();
       }
       txt += c;
     }
     return txt;
   };
 });
 app.controller('namesCtrl', function($scope) {
   $scope.names = ['Jani', 'Carl', 'Margareth', 'Hege', 'Joe', 'Gustav', 'Birgit', 'Mary', 'Kai'];
 });
 </script>
~~~

 - myFormat필터는 다른 모든 문자를 대문자로 포맷한다.
