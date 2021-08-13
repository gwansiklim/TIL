# seed란?

seed는 서버가 시작될 때 애플리케이션이 가지고 있어야 할 정적인 데이터들을 DB에 추가해주는 기능을 의미합니다.<br/>
단어 그대로 씨앗을 뿌리는 것이죠.

___

## seed 사용 할 시 명령어

```
$ npx sequelize-cli seed:generate --name user //시드 생성 명령어
$ npx sequelize-cli db:seed:all //시드 실행 명령어
$ npx sequelize-cli db:seed:undo //최근 시드 취소 명령어
$ npx sequelize-cli db:seed:undo --seed name-of-seed-as-in-data  //특정 시드 취소 명령어
$ npx sequelize-cli db:seed:undo:all //모든 시드 취소 명령어
```
___


## seed 사용 법

위의 시드생성 명령어를 통해 db에서 사용하는 테이블 명칭을 단수로 바꿔 주며, 각각 하나씩 생성을 해준다.

<img width="161" alt="스크린샷 2021-08-14 오전 1 48 35" src="https://user-images.githubusercontent.com/85220179/129392830-7012a661-1d77-4f10-903b-05ac52c639d3.png">

위의 사진은 나의 테이블별 시드생성을 한 것이다.

그리고 나서 파일을 눌러서 들어가서 각각의 테이블에 저장할 정보들을 써주면 된다. <br/>
이때, <br/>
up 프로퍼티
seed를 생성할 때 수행할 로직

<img width="760" alt="스크린샷 2021-08-14 오전 1 55 39" src="https://user-images.githubusercontent.com/85220179/129393797-c70ef4fa-f082-4670-9fc0-edaf843e9e25.png">

down 프로퍼티<br/>
seed를 되돌릴 때 수행할 로직<br/>

<img width="737" alt="스크린샷 2021-08-14 오전 1 55 57" src="https://user-images.githubusercontent.com/85220179/129393828-56d7250f-cf8f-4b61-8b94-919d6eef1ccd.png">


이런식으로 각각의 시드를 만들어준 것을 정의 해주고, 작성이 완료 된 후에는 시드 실행 명령어를 써주면 데이터들이 들어가는 걸 볼수 있다.

<img width="1028" alt="스크린샷 2021-08-14 오전 1 53 40" src="https://user-images.githubusercontent.com/85220179/129393903-2176af43-6cff-4464-b55b-579a46dbc206.png">
