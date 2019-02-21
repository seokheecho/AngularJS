# JavaScript_함수정리

## indexOf()
 - 내장함수 indexOf() 함수는 문자열에서 원하는 문자열을 검색하여 찾거나 아니면 배열에서 원하는 특정 배열값의 존재여부 등을 확인할 수 있다.
 - 배열의 경우 위치값을 index로 반환하는 함수이다.
 - "문자열".indexOf("찾을 문자")
<예제> Use "indexOf" function in AngularJS
~~~JavaScript
 $scope.addItem = function () {
   $scope.errortext = "";
   if (!$scope.addMe) {return;}
   if ($scope.products.indexOf($scope.addMe) == -1) {
     $scope.products.push($scope.addMe);
   } else {
     $scope.errortext = "The item is already in your shopping list.";
   }
 }
~~~
  - if 조건문에서 -1의 값을 가지는가의 여부를 확인한다.
  - indexOf()는 값을 찾고 그 결과로 숫자를 반환하는데 없는 경우 -1을 반환한다.
  - 하지만 있는 경우(존재하는 경우)에는 그 결과값으로 문자열의 시작위치에 해당하는 index를 반환해준다.
  - 이 함수의 장점이라면 매우 간단하게 해당 값을 가지고 있는지의 확인해서 위치를 반환하기 때문에 코드가 간결하다는 점이다.
  ** ! -1이 의미하는 것
  - 여기서는 -1을 확인값으로 사용하였는데 그 이유는 만약에 특정 문자열이 해당하는 텍스트 안에서 찾았다면 if 문에서 절대 -1이 될 수 없는 0 이상의 양수 값이기 때문이다.
  - 그래서 -1은 값이 없음을 의미하게된다.
