# Docker에 mysql연결

```
docker run --rm -p 3306:3306 --name test-db -e MYSQL_ROOT_PASSWORD=***** mysql:5.7mysqld --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```
설치 후 사진과 같이 연결이 되었으면 성공
<img width="1273" alt="스크린샷 2021-08-13 오전 1 08 24" src="https://user-images.githubusercontent.com/85220179/129230568-1159b491-2b7b-4a0c-a679-5a96d6e83985.png">

___

# vscode 연결 하기

* vscode에 mysql설치를 해준다
```
$ npm i mysql -S

$ npm i sequelize mysql2 -S

$ npm i sequelize-cli -D
```
그리고 나서 sequelize-cli를 설치 한다.
```
npx sequelize init
```
설치 후 config, models, migrations, seeders 생성 됨.

<img width="224" alt="스크린샷 2021-08-13 오전 1 15 44" src="https://user-images.githubusercontent.com/85220179/129231739-f1d85035-50e0-40c3-be94-fdb3d353675f.png">

___

# 데이터 베이스 생성 명령어
```
npx sequelize db:create
```
___

# 모델 생성하기

```
npx sequelize model:generate --name User --attributes email:string,nickname:string,password:string
npx sequelize model:generate --name Cart --attributes userId:integer //관계형 연결 할때는 주요키를 넣어준다.
```
___

# 테이블 생성, 삭제
```
npx sequelize db:migrate //생성
npx sequelize db:migrate:undo //삭제
```

