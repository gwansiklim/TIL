# Swagger란
___

* 스웨거는 Web API 문서화를 위한 도구이다.
* 스웨거 홈페이지(https://swagger.io)에서는 스웨거를 OAS(Open API Specification)이라고 소개하고 있다.
* 말 그대로 API들이 가지는 명세(Spec)을 관리하기 위한 프로젝트이다.
* Web API를 수동으로 문서화 하는 것은 굉장히 힘든일인데, Web API의 스펙이 변경되었을 대 문서 역시 변경되어야 하는데 이를 유지하는 것이 쉽지 않다.
* Swagger를 사용하면 Web API가 수정되더라도 문서가 자동으로 갱신 되기 때문에 편리하다.

## Swagger를 사용하는 이유
___

Web API를 이용하는 개발자가 Web API가 만들어질 때까지 기다린다면 작업이 상당히 느려질 수 있다.<br/>
Web API를 만드는 개발자와 Web API를 사용하는 사람 간에 미리 명세를 정의하고 공유할 수 있다면 개발이 상당히 편리해질 것이다.<br/>
이러한 것들을 편리하게 해주는 도구 중에 하나가 "스웨거"이다.<br/>

## Swagger를 사용 했을 때 페키지
___

* swagger-ui-express
* swagger-autogen

## swagger-autogen사용 방법
___
1. 위 2개의 패키지를 install을 해준다.

2. app.js 메인 서버에 require해주기
```
const swaggerUi = require("swagger-ui-express");
const swaggerFile = require("./swagger-output");


app.use("/swagger", swaggerUi.serve, swaggerUi.setup(swaggerFile));
```

3. swagger.js 파일 생성
```
const swaggerAutogen = require("swagger-autogen")();

const doc = {
  info: {
    title: "My API",
    description: "Description",
  },
  host: "localhost:3000",
  schemes: ["http"],
};

const outputFile = "./swagger-output.json";
const endpointsFiles = [
  "./app.js"
];

swaggerAutogen(outputFile, endpointsFiles, doc);
```
4. 명령어 실행
``` node ./swagger.js ```
명령어를 실행 하면 파일 목록에 swagger-output.js가 생성이 되어 있다.
그곳에 각각의 기능에 tpye과 properties를 정의를 해준다.

5. 서버 시작 후 접속 (localhost:3000/swagger)
로컬 서버는 각각 지정해준 로컬로 바꾸어 주고 실행을 해준다.

![image](https://user-images.githubusercontent.com/85220179/128411002-79ba214a-9297-40fd-92a6-7683d2b09657.png)

6. type과 properties 사용방법
___

<img width="880" alt="스크린샷 2021-08-09 오후 3 45 29" src="https://user-images.githubusercontent.com/85220179/128668928-241dd975-6ceb-460e-9219-f1dd2c0732c5.png">

위 사진과 같이 autogen을 사용하면 tags 와 parameters안에 빈 값이 있는 경우가 있을 것이다.<br/>
tags안 사진과 같이 해당 주소에서 사용할 대표이름(?)을 정해주는 것이고, <br/>
description 같은 경우에는 api파일을 눌러 열면 그안에서 사용할 이름을 써줄 떄 사용하는 것이다.<br/>
마지막으로 parrmeters안에는 사진과 같이 사용할 스키마를 적용하여 내가 사용하고자 하는 api에 관한 내용을 써준다.

<img width="1439" alt="스크린샷 2021-08-09 오후 5 18 20" src="https://user-images.githubusercontent.com/85220179/128677507-6becd098-5f49-42b3-af1c-fd6560c893b7.png">
위 사진과 같이 생기는것을 볼수 있을 것이다.
