# Jest 설치
___

```
$ npm install jest --save-dev
$ npm install supertest --save-dev
```
설치 후 package.json파일로 가서 바꿔주기.

<img width="374" alt="스크린샷 2021-09-02 오후 2 40 40" src="https://user-images.githubusercontent.com/85220179/131788216-f128d5a7-6450-4632-b492-f3042b4a8719.png">

스크립트에서 test부분을 jest로 넣어준다.

## 실행 명령어
___

```
$ npm test
또는
$ npm test 폴더명or파일명
```

를 하면 

<img width="930" alt="스크린샷 2021-09-02 오후 2 51 36" src="https://user-images.githubusercontent.com/85220179/131789371-d507761b-e26d-419a-be54-a676a72c4de6.png">

사진과 같이 실패와 패쓰에 관련하여 결과물을 알 수 있게 보여준다.


## 사용 방법
___

이제 내가 작성한 코드나 혹은 앞으로 작업할 코드에 대한 코드테스트를 진행하기 위해서는 testcode파일을 생성해서 작업을 해야한다.

```
//testcode.js
//추가
const request = require("supertest");
const app = require("../app");
const clearData = require("./clearData")
const { test, expect } = require("@jest/globals");


test("GET /api/post 경로에 요청했을 떄 Authorization 헤더가 없을 경우 실패 (401)", async () => { //이런식으로 해당 테스할 주소 또는 무엇을 테스트할지에 대해 작성해준다.
    const response = await request(app)
        .get("/api/post")   //해당 검사할 주소
        .send(
        {
          postId: 1,
        });  //보낼 데이터들
    expect(response.status).toEqual(401);
});
```
위와 같이 작성해준다. 본인은 false가 나올 때마다 api문서나 내가 작성한 코드들을 보면서 에러코드가 잘 작성이 되었는지에 대해 체크를 하고
오타나 정보를 잘 작성하였는지를 꼼꼼히 다시 찾아보면서 수정하였습니다.
