- 보안을 위해 3306 포트번호를 AWS 보안그룹에서 열어주지 않음.

$ npm i sequelize mysql2 sequelize-cli express mysql socket.io joi nunjucks jsonwebtoken chokidar

 - Sequelize를 기반으로 Node.js를 사용하기 위해 다운로드 하는 모듈들
 - 

$ npm install -g pm2

 - AWS가 종료되더라도 Node.js 서버가 실행되기 위해 pm2를 설치 


$ sudo apt-get update

$ sudo apt-get install mysql-server

$ sudo mysql

mysql> use mysql;
 - mysql Database에 접속한다.

mysql> select user, host, authentication_string from user;
 - DB의 존재하는 User의 목록을 출력시켜준다.

mysql> alter user 'root'@'localhost' identified with mysql_native_password by '1234';
 - root@localhost 아이디의 비밀번호를 1234로 지정한다.

mysql> exit
 - 접속중인 sudo 아이디에서 로그아웃한다.

$ sudo mysql -u root -p
$ 1234
 - 정상 동작하는 mysql을 확인


mysql> exit

$ npx sequelize db:create
 - Sequelize의 설정 파일을 기준으로 DB를 생성

$ npx sequelize db:migrate
 - Sequelize의 설정 파일을 기준으로 Table을 생성

$ node app.js
 - 정상 작동하는 서버를 확인할 수 있음


-- DB의 한글 깨짐 수정

$ whereis mysql;
 - mysql을 실행하는 파일이 어디에 위치해있는지 확인

$ sudo vi /etc/mysql/my.cnf
 - mysql 설정 파일인 my.cnf 파일에서 utf8 형식으로 캐릭터 셋을 변경한다.

 

vi에서 수정하기위해 (I, A) 키를 눌러 입력모드로 설정한다.
맨밑줄에 삽입후 저장 (:wq)
[mysql]
default-character-set = utf8

[client]
default-character-set = utf8

[mysqld]
character-set-server = utf8
collation-server = utf8_general_ci
init_connect=’SET NAMES utf8’


$ sudo service mysql restart;
 - my.cnf파일을 수정후 mysql을 재시작한다.

$ mysql -u root -p 
$ 1234


mysql> status 

Server characterset:    utf8
Db     characterset:    utf8
Client characterset:    utf8
Conn.  characterset:    utf8
 - Server, Db가 utf-8로 설정되어 있는 것을 확인할 수 있음


mysql> SHOW CREATE TABLE Users;
 -  ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=latin1
 -  Users 테이블의 캐릭터 셋이 latin1로 설정된 것을 확인할 수 있다.


mysql> ALTER TABLE Users CONVERT TO CHARACTER SET UTF8;
mysql> ALTER TABLE Posts CONVERT TO CHARACTER SET UTF8;
mysql> ALTER TABLE Comments CONVERT TO CHARACTER SET UTF8;
 - 모든 테이블의 캐릭터 셋을 UTF8로 변경한다.

mysql> SHOW CREATE TABLE Users;
 - 정상적으로 UTF8로 변경된 캐릭터 셋을 확인할 수 있다.

mysql> exit

$ node app.js 
 - 정상적으로 한글이 입력되는것을 확인 할 수 있다.




$ sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000
 - 80번 포트로 들어오는 클라이언트를 3000번 포트로 보냄


$ sudo pm2 start app.js
 - pm2로 AWS의 콘솔창을 종료하더라도 실행되고있도록 설정한다.

$ pm2 delete 0
 - pm2로 동작중인 첫번째 서버를 종료한다.



-- AWS EC2 DB 외부 접속 설정법
AWS 보안 그룹에서 3306 포트를 전부 열어줘야한다.

$ sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
 bind-address 값을 127.0.01 > 0.0.0.0으로 수정


$ service mysql restart
 - mysql 서버 재시작

 

$ mysql -u root -p

$ 1234

mysql> grant all privileges on *.* to root@'%' identified by '1234';
 - 어느 아이피 접속하든 상관없이 root 계정에 모든 권한을 할당한다
