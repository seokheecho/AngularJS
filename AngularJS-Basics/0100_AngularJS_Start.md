# AngularJS Start

## [AngularJS]
 - AngularJS는 새로운 속성들로 HTML을 확장한다.
 - AngularJS는 SPA(Single Page Application)에 이상적이다.
 - AngularJS는 배우기 쉽다!

## [AngularJS 연혁]
 - AngularJS 버전 1.0은 2012 년에 출시
 - Google 직원 인 Miško Hevery는 2009 년 AngularJS에서 작업하기 시작
 - 그 아이디어는 매우 잘 드러났으며 프로젝트는 현재 Google에서 공식적으로 지원


### 예제
~~~html
<!DOCTYPE html>
<html lang="en-US">
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
    <p>Name : <input type="text" ng-model="name"></p>
    <h1>Hello {{name}}</h1>
</div>

</body>
</html>
~~~
