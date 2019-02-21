# HTML_CSS_JavaScript_기타정리

## class - id - name
 - class : 주 목적이 css에서 스타일을 주기 위해 다수의 선택자로 활용되기 위함이다.
 - id : 주 목적이 css에서 스타일을 주기 위해 하나의 선택자로 활용되기 위함이다.
 - name : 폼 요소들을 제어하기 위함이다.(데이터를 다루기 위함)
 ** 그 밖에 name의 용도로는 본문 내에 이동하는데 사용
 https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_a_name
 ** 또한 name 자체는 크로스브라우징 이슈도 있고 해서, 잘 알아보고 쓰자!
<예제>
~~~HTML
<div class ="abc"></div>
<div class ="abc"></div>

<div id ="abc1"></div>
<div id ="abc2"></div>
~~~
위 HTML에 스타일을 주기 위해 이름을 불러오는 방법
~~~CSS
.abc{ }
~~~
~~~CSS
#abc1{ }
#abc2{ }
~~~
