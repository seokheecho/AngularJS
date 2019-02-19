# AngularJS Validation
 - AngularJS는 입력 데이터(input data)의 유효성을 검사 할 수 있다.

## [Form Validation]
 - AngularJS는 클라이언트 측(client-side) 형식 검증(form validation)을 제공한다.
 - AngularJS는 양식 및 입력 필드 (입력, 텍스트 영역, 선택)의 상태를 모니터링하고 사용자에게 현재 상태를 알릴 수 있게 한다.
 - AngularJS는 접촉했는지 또는 수정했는지 여부에 대한 정보도 보유하고 있다.
 - 표준 HTML5 속성을 사용하여 입력의 유효성(validate input)을 검사하거나, 자체 검증 기능(own validation functions)을 만들 수 있다.<br>
** 클라이언트 측 유효성 검사만으로는 사용자 입력을 보호 할 수 없다. 서버 측 유효성 검사도 필요하다.


## [Required]
 - HTML5 속성(attribute) `required`을 사용하여 입력 필드(input field)를 작성하도록 지정해라.
 - 입력란은 필수 항목이다.

~~~HTML
<body ng-app="">
<p>Try writing in the input field:</p>
<form name="myForm">
<input name="myInput" ng-model="myInput" required>
</form>
<p>The input's valid state is:</p>
<h1>{{myForm.myInput.$valid}}</h1>
</body>
~~~


## [E-mail]
 - 그 값이 email이어야 함을 지정하려면 HTML5 type `email`을 사용해라.
 - 입력 필드(input field)는 email 이어야한다.

~~~HTML
<body ng-app="">
<p>Try writing an E-mail address in the input field:</p>
<form name="myForm">
<input type="email" name="myInput" ng-model="myInput">
</form>
<p>The input's valid state is:</p>
<h1>{{myForm.myInput.$valid}}</h1>
<p>Note that the state of the input field is "true" before you start writing in it, even if it does not contain an e-mail address.</p>
</body>
~~~


## [Form State and Input State]
 - AngularJS는 양식과 입력 필드의 상태를 지속적으로 업데이트한다.
 - 입력 필드의 상태는 다음과 같다.

 - `$untouched` : 필드(field)에 아직 터치되지 않았습니다.
 - `$touched` : 필드(field)에 터치가 되었습니다.
 - `$pristine` : 필드(field)가 아직 수정되지 않았습니다.
 - `$dirty` : 필드(field)가 수정되었습니다.
 - `$invalid` : 필드(field) 내용이 유효하지 않습니다.
 - `$valid` : 필드(field) 내용이 유효합니다.

 - 이들은 입력 필드(input field)의 모든 속성이며 true 또는 false 중 하나이다.

 - 양식의 상태는 다음과 같다.

 - `$pristine` : 필드(field)가 아직 수정되지 않았습니다.
 - `$dirty` : 하나 이상의 수정되었습니다.
 - `$invalid` : 양식 내용(form content)이 유효하지 않습니다.
 - `$valid` : 양식 내용(form content)이 유효합니다.
 - `$submitted` : 양식 제출

 - 이들은 모두 폼(form)의 속성(properties)이며, true 또는 false 둘 중 하나이다.

 - 이 상태를 사용하여 의미있는 메시지를 사용자에게 표시 할 수 있다. 예를 들어, 필드가 필수이고 사용자가 필드를 비워두면 사용자에게 경고를 제공해야한다.
 - 필드를 터치했는데 비어있는 경우 오류 메시지 표시 :

~~~HTML
<body ng-app="">
<p>Try leaving the first input field blank:</p>
<form name="myForm">
<p>Name:
<input name="myName" ng-model="myName" required>
<span ng-show="myForm.myName.$touched && myForm.myName.$invalid">The name is required.</span>
</p>
<p>Address:
<input name="myAddress" ng-model="myAddress" required>
</p>
</form>
<p>We use the ng-show directive to only show the error message if the field has been touched AND is empty.</p>
</body>
~~~


## [CSS Classes]
 - AngularJS는 상태에 따라 양식(forms)과 입력란(input fields)에 CSS 클래스를 추가한다.
 - 다음 클래스는 입력필드(input fields)에 추가되거나 입력 필드에서 제거된다.

 - `ng-untouched` : 필드(field)에 아직 터치되지 않았습니다.
 - `ng-touched` : 필드(field)에 터치가 되었습니다.
 - `ng-pristine` : 필드(field)가 아직 수정되지 않았습니다.
 - `ng-dirty` : 필드(field)가 수정되었습니다.
 - `ng-valid` : 필드 내용(field content)이 유효합니다.
 - `ng-invalid` : 필드 내용(field content)이 유효하지 않습니다.
 - `ng-valid-key` : 각 검증을 위한 하나의 열쇠 . 예) `ng-valid-required` 유효성을 검사해야하는 항목이 두 개 이상인 경우 유용하다.
 - `ng-invalid-key` : 예) `ng-invalid-required`

 - 양식(form)에 다음 클래스가 추가되거나 폼(form)에서 제거된다.

 - `ng-pristine` : 필드(field)가 아직 수정되지 않았습니다.
 - `ng-dirty` : 필드(field)가 수정되었습니다.
 - `ng-valid` : 필드 내용(field content)이 유효합니다.
 - `ng-invalid` : 필드 내용(field content)이 유효하지 않습니다.
 - `ng-valid-key` : 각 검증을 위한 하나의 열쇠 . 예) `ng-valid-required` 유효성을 검사해야하는 항목이 두 개 이상인 경우 유용하다.
 - `ng-invalid-key` : 예) `ng-invalid-required`

 - 클래스가 나타내는 값이  false이면 클래스가 제거된다.
 - 이러한 클래스의 스타일을 추가하여 application에 보다 직관적인 사용자 인터페이스를 제공하자.
 - 표준 CSS를 사용하여 스타일 적용 :
~~~HTML
<style>
input.ng-invalid {
    background-color:pink;
}
input.ng-valid {
    background-color:lightgreen;
}
</style>
<body ng-app="">
<p>Try writing in the input field:</p>
<form name="myForm">
<input name="myName" ng-model="myName" required>
</form>
<p>The input field requires content, and will therefore become green when you write in it.</p>
</body>
~~~
 - 형식은 다음과 같이 스타일을 지정할 수도 있다.

 - unmodified (pristine) forms 및 modified forms에 스타일 적용 :
~~~HTML
<style>
form.ng-pristine {
    background-color:lightblue;
}
form.ng-dirty {
    background-color:pink;
}
</style>
<body ng-app="">
<form name="myForm">
<p>Try writing in the input field:</p>
<input name="myName" ng-model="myName" required>
<p>The form gets a "ng-dirty" class when the form has been modified, and will therefore turn pink.</p>
</form>
</body>
~~~


## [Custom Validation]
 - 자신의 검증 함수를 생성하는 것은 좀 더 까다롭다. application에 새로운 지시문을 추가하고 특정 지정된 인수가 있는 함수 내에서 유효성 검사를 처리해야한다.
 - 사용자 지정 유효성 검사 함수가 포함 된 사용자 지정 지시문을 만들고 이(my-directive)를 사용하여 참조하자.
 - 값에 문자 "e"가 포함 된 경우에만 필드가 유효하다. :
~~~HTML
<body ng-app="myApp">
<p>Try writing in the input field:</p>
<form name="myForm">
<input name="myInput" ng-model="myInput" required my-directive>
</form>
<p>The input's valid state is:</p>
<h1>{{myForm.myInput.$valid}}</h1>
<script>
var app = angular.module('myApp', []);
app.directive('myDirective', function() {
    return {
        require: 'ngModel',
        link: function(scope, element, attr, mCtrl) {
            function myValidation(value) {
                if (value.indexOf("e") > -1) {
                    mCtrl.$setValidity('charE', true);
                } else {
                    mCtrl.$setValidity('charE', false);
                }
                return value;
            }
            mCtrl.$parsers.push(myValidation);
        }
    };
});
</script>
<p>The input field must contain the character "e" to be consider valid.</p>
</body>
~~~
 ** 예제설명 - Example Explained:
 - HTML에서는 새로운 지시어가 my-directive 속성을 사용하여 참조된다.
 - 자바 스크립트에서 우리는 새로운 지시어 myDirective를 추가한다.
 - ** 지시문의 이름을 지정할 때는 낙타표기법(camel case name)을 사용해야 하지만, 호출 할 때는 -분리 된 이름을 사용해야 한다는 것을 기억하라.
 - ** `script` : myDirective <=> `html` : my-directive
 - 그런 다음 ngModelngModelController 인 필요한 객체를 반환해라.
 - 어떤 인자를 취하는 링크 함수를 만든다. 네번째 인자 mCtrl는 ngModelController,
 - 그런 다음 myValidation하나의 인수를 취하는 이 함수의 경우 명명 된 함수를 지정해라. 이 인수는 입력 요소의 값이다.
 - 값에 문자 "e"가 포함되어 있는지 테스트하고 모델 컨트롤러의 유효성을 true 또는 false 로 설정한다.
 - 마지막으로, 다른 함수의 배열에 함수를 mCtrl.$parsers.push(myValidation);추가 myValidation할 것이며, 입력 값이 바뀔 때마다 실행될 것이다.


## [Validation Example]
~~~HTML
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>  
<body>

<h2>Validation Example</h2>

<form ng-app="myApp" ng-controller="validateCtrl"
name="myForm" novalidate>

<p>Username:<br>
<input type="text" name="user" ng-model="user" required>
<span style="color:red" ng-show="myForm.user.$dirty && myForm.user.$invalid">
<span ng-show="myForm.user.$error.required">Username is required.</span>
</span>
</p>

<p>Email:<br>
<input type="email" name="email" ng-model="email" required>
<span style="color:red" ng-show="myForm.email.$dirty && myForm.email.$invalid">
<span ng-show="myForm.email.$error.required">Email is required.</span>
<span ng-show="myForm.email.$error.email">Invalid email address.</span>
</span>
</p>

<p>
<input type="submit"
ng-disabled="myForm.user.$dirty && myForm.user.$invalid ||  
myForm.email.$dirty && myForm.email.$invalid">
</p>

</form>

<script>
var app = angular.module('myApp', []);
app.controller('validateCtrl', function($scope) {
    $scope.user = 'John Doe';
    $scope.email = 'john.doe@gmail.com';
});
</script>

</body>
</html>
~~~
 - ** HTML 양식 속성 인 novalidate 는 기본 브라우저 유효성 검증을 사용 불가능하게하는 데 사용됩니다.

 ** 예제설명 - Example Explained:
 - AngularJS 지시어 `ng-model`은 입력 요소를 모델에 바인딩한다.
 - 모델 객체(model object)에는 : user 와 email 두 가지 속성이 있다.
 - `ng-show` 때문에 user 와 email이 `$dirty` 및 `$invalid` 인 경우에만 color : red로 표시된다.
