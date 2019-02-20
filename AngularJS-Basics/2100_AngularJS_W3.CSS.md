# AngularJS and W3.CSS
 - AngularJS와 함께 w3.css 스타일 시트를 쉽게 사용할 수 있습니다. 이 장에서는 방법을 보여준다.


## [W3.CSS]
 - AngularJS application에 W3.CSS를 포함 시키려면 문서 머리 부분에 다음 줄을 추가해라.

 <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
 - W3.CSS를 배우고 싶다면 W3.CSS 튜토리얼을 방문하자.
(https://www.w3schools.com/w3css/default.asp)
 - 다음은 전체 HTML 예제이며 모든 AngularJS 지시문과 W3.CSS 클래스가 설명되어 있다.


## [HTML Code]
~~~HTML
<!DOCTYPE html>
<html>
<link rel="stylesheet" href="/w3css/4/w3.css">
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body ng-app="myApp" ng-controller="userCtrl">

<div class="w3-container">

<h3>Users</h3>

<table class="w3-table w3-bordered w3-striped">
  <tr>
    <th>Edit</th>
    <th>First Name</th>
    <th>Last Name</th>
  </tr>
  <tr ng-repeat="user in users">
    <td>
      <button class="w3-btn w3-ripple" ng-click="editUser(user.id)">&#9998; Edit</button>
    </td>
    <td>{{ user.fName }}</td>
    <td>{{ user.lName }}</td>
  </tr>
</table>
<br>
<button class="w3-btn w3-green w3-ripple" ng-click="editUser('new')">&#9998; Create New User</button>

<form ng-hide="hideform">
  <h3 ng-show="edit">Create New User:</h3>
  <h3 ng-hide="edit">Edit User:</h3>
    <label>First Name:</label>
    <input class="w3-input w3-border" type="text" ng-model="fName" ng-disabled="!edit" placeholder="First Name">
  <br>
    <label>Last Name:</label>
    <input class="w3-input w3-border" type="text" ng-model="lName" ng-disabled="!edit" placeholder="Last Name">
  <br>
    <label>Password:</label>
    <input class="w3-input w3-border" type="password" ng-model="passw1" placeholder="Password">
  <br>
    <label>Repeat:</label>
    <input class="w3-input w3-border" type="password" ng-model="passw2" placeholder="Repeat Password">
  <br>
  <button class="w3-btn w3-green w3-ripple" ng-disabled="error || incomplete">&#10004; Save Changes</button>
</form>

</div>

<script src= "myUsers.js"></script>

</body>
</html>
~~~


## [Directives (Used Above) Explained]
 |AngularJS Directive|Description|
 |:-----|:-----|
 |<body ng-app | Defines an application for the <body> element |
 |<body ng-controller | Defines a controller for the <body> element |
 |<tr ng-repeat | Repeats the <tr> element for each user in users |
 |<button ng-click | Invoke the function editUser() when the <button> element is clicked |
 |<h3 ng-show | Show the <h3>s element if edit = true |
 |<h3 ng-hide | Hide the form if hideform = true, and hide the <h3> element if edit = true |
 |<input ng-model | Bind the <input> element to the application |
 |<button ng-disabled | Disables the <button> element if error or incomplete = true |


## [W3.CSS Classes Explained]
|Element|Class|Defines|
|:-----|:-----|:-----|
|<div> | w3-container | A content container |
|<table> | w3-table | A table |
|<table> | w3-bordered | A bordered table |
|<table> | w3-striped | A striped table |
|<button> | w3-btn | A button |
|<button> | w3-green | A green button |
|<button> | w3-ripple | A ripple effect when you click the button |
|<input> | w3-input | An input field |
|<input> | w3-border | A border on the input field |


## [JavaScript Code]
 - myUsers.js
~~~JavaScript
 angular.module('myApp', []).controller('userCtrl', function($scope) {
 $scope.fName = '';
 $scope.lName = '';
 $scope.passw1 = '';
 $scope.passw2 = '';
 $scope.users = [
 {id:1, fName:'Hege', lName:"Pege" },
 {id:2, fName:'Kim',  lName:"Pim" },
 {id:3, fName:'Sal',  lName:"Smith" },
 {id:4, fName:'Jack', lName:"Jones" },
 {id:5, fName:'John', lName:"Doe" },
 {id:6, fName:'Peter',lName:"Pan" }
 ];
 $scope.edit = true;
 $scope.error = false;
 $scope.incomplete = false;
 $scope.hideform = true;
 $scope.editUser = function(id) {
   $scope.hideform = false;
   if (id == 'new') {
     $scope.edit = true;
     $scope.incomplete = true;
     $scope.fName = '';
     $scope.lName = '';
     } else {
     $scope.edit = false;
     $scope.fName = $scope.users[id-1].fName;
     $scope.lName = $scope.users[id-1].lName;
   }
 };

 $scope.$watch('passw1',function() {$scope.test();});
 $scope.$watch('passw2',function() {$scope.test();});
 $scope.$watch('fName', function() {$scope.test();});
 $scope.$watch('lName', function() {$scope.test();});

 $scope.test = function() {
   if ($scope.passw1 !== $scope.passw2) {
     $scope.error = true;
     } else {
     $scope.error = false;
   }
   $scope.incomplete = false;
   if ($scope.edit && (!$scope.fName.length ||
   !$scope.lName.length ||
   !$scope.passw1.length || !$scope.passw2.length)) {
      $scope.incomplete = true;
   }
 };

 });
~~~


## [JavaScript Code Explained]
|Scope Properties|Used for|
|:-----|:-----|
|$scope.fName | Model variable (user first name) |
|$scope.lName | Model variable (user last name) |
|$scope.passw1 | Model variable (user password 1) |
|$scope.passw2 | Model variable (user password 2) |
|$scope.users | Model variable (array of users) |
|$scope.edit | Set to true when user clicks on 'Create user'. |
|$scope.hideform | Set to false when user clicks on 'Edit' or 'Create user'. |
|$scope.error | Set to true if passw1 not equal passw2 |
|$scope.incomplete | Set to true if any field is empty (length = 0) |
|$scope.editUser | Sets model variables |
|$scope.$watch | Watches model variables |
|$scope.test | Tests model variables for errors and incompleteness |
