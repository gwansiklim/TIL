## html문서로 그래프표 보여주기
___

report.json파일을 하나 생성

```
$ npx artillery run --output report.json ( 파일명 )
```

<img width="119" alt="스크린샷 2021-08-24 오후 5 02 45" src="https://user-images.githubusercontent.com/85220179/130580052-4c2cff98-4e3b-4a93-80a6-8bc705a11b62.png">

report.json 파일 생성 후 html 파일 만들어 주기

```
$ npx artillery report ./report.json
```

<img width="166" alt="스크린샷 2021-08-24 오후 5 05 58" src="https://user-images.githubusercontent.com/85220179/130580622-c31934a3-b877-412d-8143-97fdc437ee9b.png"> 

파일생성 후 화면띄워짐

<img width="1440" alt="스크린샷 2021-08-24 오후 5 05 03" src="https://user-images.githubusercontent.com/85220179/130580693-b6bf0762-2c65-4173-8ba2-665f0a834913.png">

<img width="1437" alt="스크린샷 2021-08-24 오후 5 05 21" src="https://user-images.githubusercontent.com/85220179/130580708-527f7872-e50f-4809-9c57-5b2831ebf047.png">

