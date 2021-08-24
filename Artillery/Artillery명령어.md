# Artillery란?
___

Artillery는 Node.js로 작성된 스트레스 테스트 도구이다.<br/>
그리고 서버가 얼마만큼의 부하를 견딜 수 있는지 부하 테스트를 진행하는 것.
json형식과 yml형식 2가지가 있으나, 나는 node.js로 javascript기반이기 때문에 json형식을 사용하기로 했다.<br/>
json형식을 yml형식으로 변환하는 명령어도 있어 나중에 yml형식으로 자동 변환도 할수 있다.


## Artillery설치
___

```
$ npm I artillery -D
```

## 간단 테스트
___
임의의 값을 줘 테스트를 한다.

```
$ npx artillery quick --count 100 -n 50 http://localhost:{본인 로컬 주소} //100명의 사용자가 50번씩 총 5천번을 요청한다는 뜻
```
이때 터미널을 2개 켜주고 하나는 npm start 또는 node app.js를 실행 시켜주고 하나는 아틸러리 실행할 터미널을 켜줘야 한다.

<img width="1186" alt="스크린샷 2021-08-24 오후 4 40 51" src="https://user-images.githubusercontent.com/85220179/130577033-b02b5923-a97c-4605-a68b-240ca05b4126.png">

## 공룡보여주기
___
artillery 기능중에 하나 공룡을 보여주는 기능이 있다 
```
$ ./node_modules/artillery/bin/artillery dino
```
를 입력해주면

<img width="885" alt="스크린샷 2021-08-24 오후 4 45 19" src="https://user-images.githubusercontent.com/85220179/130577559-1e12b830-a483-4953-84fb-280216fc720f.png">

공룡 모양이 나타난다.


## json 형식으로 문서 작업하기
___

<img width="1162" alt="스크린샷 2021-08-24 오후 4 51 28" src="https://user-images.githubusercontent.com/85220179/130578359-6f375451-7927-43ed-b706-a679e3b4cd36.png">

이름을 정해주는 것도 있고 여러가지 넣어주는게 있지만 나는 간단하게 테스트 할 내용만 사용했다.


## json파일 변환 명령어
___

json형식을 yml형식으로 변환하거나 yml형식을 json형식으로 변환가능하다.

```
$ npx artillery convert (artillery.json 파일명)
```

## Artillery 실행 명령어
___

```
$ npx artillery run { 파일명 }
```

<실행 후 중간보고서(?)>

<img width="963" alt="스크린샷 2021-08-24 오후 4 50 07" src="https://user-images.githubusercontent.com/85220179/130578576-f2864f5b-62b8-49c9-9687-a6109a0767ef.png">

<최종 보고서>

<img width="546" alt="스크린샷 2021-08-24 오후 4 50 45" src="https://user-images.githubusercontent.com/85220179/130578615-79094d67-52da-41df-b826-d6174e43cab4.png">

