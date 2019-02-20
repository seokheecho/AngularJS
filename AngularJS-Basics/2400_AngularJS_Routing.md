# [AngularJS Routing]
 - 이 `ngRoute` 모듈은 application이 단일 페이지 application이되도록 도와준다.

## [What is Routing in AngularJS?]
 - application의 다른 페이지로 이동하려고 하지만 페이지를 다시 로드하지 않고 application을 SPA(단일 페이지 응용 프로그램)로 만들려면 해당 `ngRoute`모듈을 사용할 수 있다.
 - `ngRoute` 모듈 경로 전체 application을 다시 로드하지 않고 다른 페이지로 application 이다.
 - "red.htm", "green.htm"및 "blue.htm"으로 이동해보자.
~~~HTML
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-route.js"></script>
<body ng-app="myApp">
<p><a href="#/!">Main</a></p>
<a href="#!red">Red</a>
<a href="#!green">Green</a>
<a href="#!blue">Blue</a>
<div ng-view></div>
<script>
var app = angular.module("myApp", ["ngRoute"]);
app.config(function($routeProvider) {
    $routeProvider
    .when("/", {
        templateUrl : "main.htm"
    })
    .when("/red", {
        templateUrl : "red.htm"
    })
    .when("/green", {
        templateUrl : "green.htm"
    })
    .when("/blue", {
        templateUrl : "blue.htm"
    });
});
</script>
<p>Click on the links to navigate to "red.htm", "green.htm", "blue.htm", or back to "main.htm"</p>
</body>
~~~


## [What do I Need?]
 - application을 Routing 할 수 있도록하려면 AngularJS Route 모듈을 포함해야한다.

~~~HTML
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular-route.js"></script>
~~~
 - 그런 다음 ngRoute application 모듈에 as a dependency를 추가해야한다.
~~~JavaScript
var app = angular.module("myApp", ["ngRoute"]);
~~~
 - 이제 application에 제공된 $routeProvider을 Route 모듈에 액세스 할 수 있다.
 - $routeProvider 사용하여 application에서 다른 경로를 구성해보자.

~~~JavaScript
app.config(function($routeProvider) {
  $routeProvider
  .when("/", {
    templateUrl : "main.htm"
  })
  .when("/red", {
    templateUrl : "red.htm"
  })
  .when("/green", {
    templateUrl : "green.htm"
  })
  .when("/blue", {
    templateUrl : "blue.htm"
  });
});
~~~


## [Where Does it Go?]
 - application에는 Routing에서 제공하는 내용을 넣을 컨테이너가 필요한다.
 - 이 컨테이너가 `ng-view` 지시어이다.
 - `ng-view` application에 지시문을 포함시키는 세 가지 다른 방법이 있다.

~~~HTML
<div ng-view></div>
~~~
~~~HTML
<ng-view></ng-view>
~~~
~~~HTML
<div class="ng-view"></div>
~~~
 - application에는 하나의 `ng-view` 지시문만있을 수 있으며, 이 지시문은 경로에서 제공하는 모든 보기(view)에 대한 자리 표시이다.
(Applications can only have one ng-view directive, and this will be the placeholder for all views provided by the route.)


##[$routeProvider]
 - `$routeProvider`를 사용하면 사용자가 링크를 클릭 할 때 표시 할 페이지를 정의 할 수 있다.
 - 정의 $routeProvider:
~~~HTML
<body ng-app="myApp">
<p><a href="#/!">Main</a></p>
<a href="#!london">City 1</a>
<a href="#!paris">City 2</a>
<p>Click on the links to read about London and Paris.</p>
<div ng-view></div>
<script>
var app = angular.module("myApp", ["ngRoute"]);
app.config(function($routeProvider) {
    $routeProvider
    .when("/", {
        templateUrl : "main.htm"
    })
    .when("/london", {
        templateUrl : "london.htm"
    })
    .when("/paris", {
        templateUrl : "paris.htm"
    });
});
</script>
</body>
~~~
 - application $routeProvider의 config메서드를 사용하여 정의하라. config메서드에 등록 된 작업은 application이 로드 될 때 수행된다.


## [Controllers]
 - $routeProvider으로 당신은 또한 각 "보기(View)"에 대한 컨트롤러를 정의 할 수 있다.

~~~HTML
<body ng-app="myApp">
<p><a href="#/!">Main</a></p>
<a href="#!london">City 1</a>
<a href="#!paris">City 2</a>
<p>Click on the links.</p>
<p>Note that each "view" has its own controller which each gives the "msg" variable a value.</p>
<div ng-view></div>
<script>
var app = angular.module("myApp", ["ngRoute"]);
app.config(function($routeProvider) {
    $routeProvider
    .when("/", {
        templateUrl : "main.htm",
    })
    .when("/london", {
        templateUrl : "london.htm",
        controller : "londonCtrl"
    })
    .when("/paris", {
        templateUrl : "paris.htm",
        controller : "parisCtrl"
    });
});
app.controller("londonCtrl", function ($scope) {
    $scope.msg = "I love London";
});
app.controller("parisCtrl", function ($scope) {
    $scope.msg = "I love Paris";
});
</script>
</body>
~~~

 - "london.htm"과 "paris.htm"은 일반적인 HTML 파일로, AngularJS application의 다른 HTML 섹션과 마찬가지로 AngularJS 표현식을 추가 할 수 있다.

 - 파일은 다음과 같다.

 - london.htm
~~~HTML
<h1>London</h1>
<h3>London is the capital city of England.</h3>
<p>It is the most populous city in the United Kingdom, with a metropolitan area of over 13 million inhabitants.</p>
<p>{{msg}}</p>
~~~

 - paris.htm
~~~HTML
<h1>Paris</h1>
<h3>Paris is the capital city of France.</h3>
<p>The Paris area is one of the largest population centers in Europe, with more than 12 million inhabitants.</p>
<p>{{msg}}</p>
~~~


## [Template]
 - 앞의 예제에서 우리는 `$routeProvider` 메소드의 templateUrl 속성을 사용했다.
 - 이 template속성을 사용하면 페이지를 참조하지 않고 속성 값에 직접 HTML을 쓸 수 있다.
 - 템플릿 작성 :
~~~HTML
<body ng-app="myApp">
<p><a href="#/!">Main</a></p>
<a href="#!banana">Banana</a>
<a href="#!tomato">Tomato</a>
<p>Click on the links to change the content.</p>
<p>The HTML shown in the ng-view directive are written in the template property of the $routeProvider.when method.</p>
<div ng-view></div>
<script>
var app = angular.module("myApp", ["ngRoute"]);
app.config(function($routeProvider) {
    $routeProvider
    .when("/", {
        template : "<h1>Main</h1><p>Click on the links to change this content</p>"
    })
    .when("/banana", {
        template : "<h1>Banana</h1><p>Bananas contain around 75% water.</p>"
    })
    .when("/tomato", {
        template : "<h1>Tomato</h1><p>Tomatoes contain around 95% water.</p>"
    });
});
</script>
</body>
~~~

## [The otherwise method]
 - 앞의 예제에서 우리는 $routeProvider메소드를 사용했다 .
 - otherwise 다른 사람이 일치하지 않는 경우 기본 경로인 메서드를 사용할 수도 있다.
 - "Banana"또는 "Tomato"링크를 클릭하지 않았다면 다음과 같이 알려주라.
~~~HTML
<body ng-app="myApp">
<p><a href="#/!">Main</a></p>
<a href="#!banana">Banana</a>
<a href="#!tomato">Tomato</a>
<p>Click on the links to change the content.</p>
<p>Use the "otherwise" method to define what to display when none of the links are clicked.</p>
<div ng-view></div>
<script>
var app = angular.module("myApp", ["ngRoute"]);
app.config(function($routeProvider) {
    $routeProvider
    .when("/banana", {
        template : "<h1>Banana</h1><p>Bananas contain around 75% water.</p>"
    })
    .when("/tomato", {
        template : "<h1>Tomato</h1><p>Tomatoes contain around 95% water.</p>"
    })
    .otherwise({
        template : "<h1>Nothing</h1><p>Nothing has been selected</p>"
    });
});
</script>
</body>
~~~
