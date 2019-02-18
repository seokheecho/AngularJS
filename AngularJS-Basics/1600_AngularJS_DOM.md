# AngularJS HTML DOM
 - AngularJS는 application data를 HTML DOM 요소(elements)의 속성에 바인딩하기 위한 지시문(directives)을 가지고 있다.


## [The ng-disabled Directive]
 - `ng-disabled` 지시어는 HTML 요소의 disabled 속성에 AngularJS와 application data를 결합한다.

~~~HTML
<div ng-app="" ng-init="mySwitch=true">
<p>
<button ng-disabled="mySwitch">Click Me!</button>
</p>
<p>
<input type="checkbox" ng-model="mySwitch"/>Button
</p>
<p>
{{ mySwitch }}
</p>
</div>
~~~
Application explained:

 - `ng-disabled` 지시자는 application data mySwitch에 HTML 버튼에 사용할 속성을 바인딩한다.
 - `ng-model` 지시어는 HTML 체크 박스 요소의 값에서 mySwitch 값으로 바인딩한다.
 - mySwitch 의 값이 true로 평가되면 버튼이 비활성화된다.

~~~HTML
<p>
<button disabled>Click Me!</button>
</p>
~~~
 - mySwitch 의 값이 false로 평가되면 버튼이 비활성화되지 않는다.
~~~HTML
<p>
<button>Click Me!</button>
</p>
~~~


## [The ng-show Directive]
 - `ng-show` 지시문은 HTML 요소를 숨기거나 보여준다.

~~~HTML
<div ng-app="">
<p ng-show="true">I am visible.</p>
<p ng-show="false">I am not visible.</p>
</div>
~~~

 - `ng-show` 지시문은 `ng-show` 의 값을 기반으로 HTML 요소를 표시하거나 숨긴다.
 - true 또는 false로 평가되는 식을 사용할 수 있다.

~~~HTML
<div ng-app="" ng-init="hour=13">
<p ng-show="hour > 12">I am visible.</p>
</div>
~~~

** 다음 장에서는 버튼 클릭으로 HTML 요소를 숨기는 예제가 더 있다.


## [The ng-hide Directive]
 - `ng-hide` 지시문은 HTML 요소를 숨기거나 보여준다.

~~~HTML
<div ng-app="">
<p ng-hide="true">I am not visible.</p>
<p ng-hide="false">I am visible.</p>
</div>
~~~

 - `ng-hide` 지시문은 `ng-hide` 의 값을 기반으로 HTML 요소를 표시하거나 숨긴다.
 - true 또는 false로 평가되는 식을 사용할 수 있다.

~~~HTML
<div ng-app="" ng-init="hour=13">
<p ng-hide="hour > 12">I am visible.</p>
</div>
~~~
