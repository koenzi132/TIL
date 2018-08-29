# MySQL (Database - relational DBMS)

* Oracle과는 다르게 무료이면서 오픈소스이고, 3대 데이터베이스 중 하나인 **MySQL**은 관계형 데이터베이스의 주요한 기능을 대부분 갖추고 있는 준수한 관계형 데이터베이스 시스템이다.

* <u>**관계형 데이터베이스 (relational DBMS)**</u>.

  * 데이터를 <u>**표의 형태**</u>로 정리정돈 가능. (스프레드 시트처럼.. )
    *( 사진 출처 - 생활코딩 )*

    <img width="692" alt="2018-08-29 6 33 14" src="https://user-images.githubusercontent.com/39458555/44779297-1cc8f980-abba-11e8-9b8f-65a09c2dcce0.png">

  * 정렬, 검색과 같은 작업을 빠르고 편리하고 안전하게 할 수 있음.

  * (MySQL, Oracle, SQL server, PostgreSQL, DB2, Access 등..)

----

##### MySQL 실행방법 (터미널)

* terminal 접속
* cd /usr/local/mysql/bin/  타이핑
* bin이 뜨면 - > ./mysql -uroot -p  를 타이핑 (uroot = root라는 유저 / p = password를 입력하겠다는 뜻)
* password 입력 - > connected

----------

##### MySQL의 구조

*( 사진 출처 - 생활코딩 )*

* **표 (table)** - 정보는 결국은 표에 저장이 된다.
* **데이터베이스 (database)** === **<u>스키마 (schema)</u>**
  * 폴더의 기능과 같이, <u>서로 연관된 표들을 그룹핑</u> 해서 연관되지 않은 표들과 분리함.
* **데이터베이스 서버 (database server)** - 스키마들을 담고 있는 상위 폴더같은 존재.

(MySQL을 설치한 것은 데이터베이스 서버를 설치한 것임.)

<img width="1204" alt="mysql" src="https://user-images.githubusercontent.com/39458555/44781926-95cb4f80-abc0-11e8-982c-aea6bc3239fc.png">

----------

