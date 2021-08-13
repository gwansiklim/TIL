# mysql 접속 하기

### mysql에 데이터 베이스 접속
```
docker exec -it test-db(자신의 도커에 등록되어있는 db이름) bash
```
___

### mysql 루트로 들어가기
```
mysql -u root -p
```
그 후 바로 비밀번호 창이 생기는데 자기가 설정한 비밀번호를 입력후 엔터클릭,
___

### 데이터베이스 접속

```
USE (db이름)
```

___

### 테이블 띄우기 (SELECT)

```
SELECT * FROM (테이블이름);
```
꼭 ; <-이 표시를 마지막에 붙여줘야함 마침표 같은 거라고 생각.


### 1개의 정보만 띄우기

```
select (해당 테이블 id) from (테이블 이름) where (userId=1);
```

