# 오늘 배운 것
___
* express
* middleware

## express middleware란?
___

미들웨어 함수는 req(요청) 객체, res(응답) 객체, 그리고 어플리케이션 요청-응답 사이클 도중 그 다음의 미들웨어 함수에 대한 엑세스 권한을 갖는 함수이다.<br/>
라고 docs에 명시 되어있다.<br/>
미들웨어란 간단하게 말하면 클라이언트에게 요청이 오고 그 요청을 보내기 위해 응답하려는 중간(미들)에 목적에 맞게 처리를 하는,<br/> 
말하자면 거쳐가는 함수들이라고 보면 되겠다.<br/>
미들웨어들을 어떨 때 사용하면 편리하냐면 페이지를 렌더링할 때 사용자 인증을 앞서 거친 후에 렌더링하고 싶을 때 사용자 인증 미들웨어를 작성하고 앞에 삽입하게 되면 편리하다.<br/>
혹은 로그를 먼저 남기고 싶을때도 로그를 남기는 미들웨어를 작성하고 앞서 삽입하면 편리하다.<br/>

## express middleware의 특징
___

* 모든 코드를 실행
* 다음 미들웨어 호출(미들웨어가 순차적으로 실행)
* res, req 객체 변경 가능
* 요청-응답 주기를 종료(response methods를 이용)

```
var express = require('express');
var app = express();

var myLogger = function (req, res, next) {
  console.log('LOGGED');
  next();
};

app.use(myLogger);

app.get('/', function (req, res) {
  res.send('Hello World!');
});

app.listen(3000);
```
위의 코드가 예시인데 이때 클라이언트가 루트 경로(ex. http:/localhost:3000/)로 요청을 보냈을 때
 myLogger를 먼저 거치고 myLogger는 다음 미들웨어 호출(next())함수를 지정하여 res.send("Hello World"); 코드가 담긴 미들웨어로 넘어가게 된다는 의미이다.<br/>

## Middleware 유형
___

다음과 같은 middleware 유형이 존재한다.

* 어플리케이션 레벨 미들웨어
* 라우터 레벨 미들웨어
* 오류 처리 미들웨어
* 써드파티 미들웨어


### 어플리케이션 레벨 미들웨어
___

app.use() 및 app.METHOD() 함수(*method: get, post 등등)를 이용해 app 오브젝트의 인스턴스에 바인드 시킨다.<br/>
미들웨어를 어플리케이션 영역에서 지정한 path대로 처리 가능하게 하도록 한다.<br/>
```
var app = express();

app.use(function (req, res, next) {
  console.log('Time:', Date.now());
  next();
});
```

아래의 예제와 같이 특정 경로나 http methods 에 대해서만 적용할 수도 있다.<br/>
이 함수들은 /user/:id 경로에 대해 미들웨어들이 실행된다.
```
// 모든 /user/:id 요청에 대해 작동
app.use('/user/:id', function (req, res, next) {
  console.log('Request Type:', req.method);
  next();
});

// /user/:id인 GET 요청에 대해서만 응답
app.get('/user/:id', function (req, res, next) {
  res.send('USER');
});
```
다음은 하나의 경로를 통해 일련의 미들웨어 함수를 하나의 마운트 위치에 로드하는 예가 표시되어있다.<br/> 
위의 미들웨어가 먼저 실행 된 뒤에 다음, 미들웨어가 이어 받는다.<br/>
```
app.use('/user/:id', function(req, res, next) {
  console.log('Request URL:', req.originalUrl);
  next();
}, function (req, res, next) {
  console.log('Request Type:', req.method);
  next();
});
```

### 라우터 레벨 미들웨어
___

라우터 레벨 미들웨어는 express.Router() 인스턴스에 바인드된다는 점을 제외하면 어플리케이션 레벨 미들웨어와 동일한 방식으로 작동한다.<br/>
Router객체를 이용해 router.use() 및 router.METHOD() 함수를 사용하여 라우터 레벨 미들웨어를 로드할 수 있다.<br/>
Router 객체는 그 자체가 미들웨어처럼 움직이므로 app.use()의 인수(argument)로 사용될 수 있고 또한 다른 router의 use() 메서드에서 사용될 수 있다.<br/>
var router = express.Router()로 Router 객체를 생성한 뒤에 app.use()를 사용해 마운트 시켜야지만 사용가능하다.<br/>
app.use()에서 지정한 경로와 같은 것이 들어온다면 모두 적용시켜버리기 때문에 중복이 될 가능성이 있다. <br/>
예를 들어 app.use('/apple', ...) 이 있다면 /apple, /apple/images, /apple/images/news 등에 모두 적용시켜 버린다.<br/>
router를 사용하는 이유는 특정 root url을 기점으로 기능이나 로직별로 라우팅을 나눠서 관리할 수 있다는 점이다.<br/>
user 라우터에는 다른 라우터에는 필요없는 인증 미들웨어를 따로 추가하는 등의 작업을 할 수 있다.<br/>

### 오류 처리 미들웨어
___

에러 핸들링을 하는 미들웨어는 4개의 인자를 사용해서 정의하도록 한다. (err, req, res, next)<br/>
단순히 에러 핸들링 미들웨어는 에러를 다루기 위한 미들웨어이다.<br/>
다음 포스팅때 좀 더 다루기로 한다.<br/>

###써드파티 미들웨어
___

기능적으로 express app에 미들웨어를 추가하기 위해 서드 파티 미들웨어 사용을 권고한다. <br/>
Node.js 모듈을 사용하고 싶다면 application 레벨이든 router 레벨이든 로드해서 사용하면 된다.<br/>
npm에서 install 가능하다.<br/>

