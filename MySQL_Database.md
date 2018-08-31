# MySQL (Database - relational DBMS)

* Oracle과는 다르게 무료이면서 오픈소스이고, 3대 데이터베이스 중 하나인 **MySQL**은 관계형 데이터베이스의 주요한 기능을 대부분 갖추고 있는 준수한 관계형 데이터베이스 시스템이다.

* <u>**관계형 데이터베이스 (relational DBMS)**</u>.

  * 데이터를 <u>**표의 형태**</u>로 정리정돈 가능. (스프레드 시트처럼.. )
    *( 사진 출처 : 생활코딩 - https://opentutorials.org/course/3161/19531)*

    <img width="692" alt="2018-08-29 6 33 14" src="https://user-images.githubusercontent.com/39458555/44779297-1cc8f980-abba-11e8-9b8f-65a09c2dcce0.png">

  * 정렬, 검색과 같은 작업을 빠르고 편리하고 안전하게 할 수 있음.

  * (MySQL, Oracle, SQL server, PostgreSQL, DB2, Access 등..)

----------

##### MySQL의 구조

* **표 (table)** - 정보는 결국은 표에 저장이 된다.
* **데이터베이스 (database)** === **<u>스키마 (schema)</u>**
  * 폴더의 기능과 같이, <u>서로 연관된 표들을 그룹핑</u> 해서 연관되지 않은 표들과 분리함.
* **데이터베이스 서버 (database server)** - 스키마들을 담고 있는 상위 폴더같은 존재.

(MySQL을 설치한 것은 데이터베이스 서버를 설치한 것임.)

<img width="1204" alt="mysql" src="https://user-images.githubusercontent.com/39458555/44781926-95cb4f80-abc0-11e8-982c-aea6bc3239fc.png">

*( 사진 출처 : 생활코딩 - https://opentutorials.org/course/3161/19533)*

----------

##### MySQL 서버 접속 방법 (터미널)

- terminal 접속
- cd /usr/local/mysql/bin/  타이핑
- bin이 뜨면 - > ./mysql -uroot -p  를 타이핑 (uroot = root라는 유저(u) / p = password를 입력하겠다는 뜻) 
  (일반적으로 root라는 유저는 관리자를 의미하므로, 모든 권한이 열려있다. 따라서, root를 직접적으로 데이터베이스를 다루는 것은 위험하기 때문에, 중요한 시스템이라면 별도의 사용자를 만들어서 평소에는 그 사용자로 작업하는 것을 추천한다.)
- password 입력 - > connected

---

##### MySQL 스키마(schema) 사용 방법

* CREATE DATABASE *databaseName*; ➢ 데이터베이스(스키마) 생성
* DROP DATABASE *databaseName*; ➢ 데이터베이스(스키마) 삭제
* 키보드 화살표 ↑를 누르면 이전에 썼던 명령어를 불러올 수 있음
* SHOW DATABASES; ➢ 생성된 데이터베이스(스키마)를 확인
* USE *databaseName*; ➢ 지금부터 내리는 명령이 databaseName이라는 데이터베이스(스키마)에 있는 표를 대상으로 내리는 명령이 되도록 함
* 패스워드 재설정 방법 : SET PASSWORD = PASSWORD('*yourPassword*');

------------

##### SQL과 테이블 구조

> **SQL** (**S**tructured **Q**uery **L**anguage) : 데이터베이스를 구축하고 활용하기 위해 사용하는 언어. <u>관계형 데이터 모델</u>(Relational DBMS)로 표현되는 데이터베이스를 다루는 언어로 가장 널리 사용되고 있다. 

<img width="400" alt="2018-08-29 9 40 43" src="https://user-images.githubusercontent.com/39458555/44788149-3b3bee80-abd4-11e8-8472-025eda942904.png">

<img width="400" alt="2018-08-29 9 52 12" src="https://user-images.githubusercontent.com/39458555/44788748-d1244900-abd5-11e8-9417-72df6b8d8aaa.png">

( 사진 출처 : 생활코딩 - https://opentutorials.org/course/3161/19536 )*

* 데이터베이스(스키마)에서 row(행)는 데이터 하나 하나를 의미하고, column(열)은 데이터 의 타입을 의미한다. 
  * 위 사진에서 row(행)는 2개이고, column(열)은 4개이다.

------------

##### MySQL 테이블 생성 (create table in MySQL)

( google에서 **MySQL cheat sheet**를 찾아 이용하는 것도 좋은 방법이다. )
( 아래에 나오는 datatype도 검색해서 찾아서 이용한다. )
( 참고하기 좋은 사이트 : https://www.techonthenet.com/mysql/datatypes.php )
( length의 경우 글자수를 얼마까지 노출시킬 것인가를 나타내는 것이다. 보통 11을 이용.)

* CREATE TABLE *tableName* (
  columnName datatype(length) <u>NOT NULL</u> <u>AUTO_INCREMENT</u>,
  columnName datatype(length) )

이런 식으로...

( 사진 출처 : 생활코딩 - https://opentutorials.org/course/3161/19537 )

<img width="400" alt="2018-08-30 3 47 43" src="https://user-images.githubusercontent.com/39458555/44834405-14c99200-ac6c-11e8-91d5-4cddac16fb7f.png">

**<u>NOT NULL</u>** : 빈 값을 허용하지 않겠다는 선언. ( → **<u>NULL</u>** 로 해주면, 값이 없는 것을 허용한다 라는 의미.)

**<u>AUTO_INCREMENT</u>** : 자동으로 증가시킴 ( 예를 들면, id 라는 column이 숫자 1,2,3,4,, 이런식으로 되어있을 경우, 새로운 데이터가 들어올 때 해당 데이터의 id 값이 5로 바로 설정되게끔..)

**<u>VARCHAR(size)</u>** (**datatype**): 입력된 값에서 정해진 size(글자수)만큼만 기록하고 나머지는 버려버리는 기능.

**<u>PRIMARY KEY( )</u>** : 생성되는 테이블에 메인 column이 무엇인지 설정해 주는 것.
(primary key는 성능적인 측면, **<u>중복을 방지</u>**하는 측면의 두 가지 측면에서 사용된다. = <u>"해당 column의 값들은 중요하니까 다른 column들과 달리 값이 중복되면 안돼!"</u> 해주는 것.)

-----------

#### DATABASE( not schema ) 의 CRUD

* **C**reate (생성) - 가장 중요. 반드시 존재.
* **R**ead (읽는다) - 중요. 반드시 존재.
* **U**pdate (수정) - 없을 수도 있음.
* **D**elete (삭제) - 없을 수도 있음.

♻︎ <u>데이터베이스가 무엇이건간에 가지고 있는 네 가지의 작업.</u>

♻︎ <u>어떤 데이터베이스를 만나건, 그 데이터베이스에서 create와 read가 무엇인지를 따져보는 것이 가장 중요하다.</u>

-------------

##### SQL의 INSERT 구문 ( Create 부분 )

<img width="488" alt="2018-08-31 5 19 00" src="https://user-images.githubusercontent.com/39458555/44901319-0188f600-ad42-11e8-95a2-255a59e5a826.png">

* <u>**DESC *tableName***</u> : 현재 테이블에 대한 정보가 나옴.

<img width="400" alt="2018-08-31 5 22 43" src="https://user-images.githubusercontent.com/39458555/44901489-7f4d0180-ad42-11e8-826d-8f78260b99fd.png">

<img width="641" alt="2018-08-31 5 27 18" src="https://user-images.githubusercontent.com/39458555/44901718-229e1680-ad43-11e8-855d-a839ec897813.png">

> 이런 식으로 데이터를 입력. VALUES 중에 NOW() 라는 것은, 입력하는 현재 날짜와 시간을 자동으로 채워주는 함수임. ( 여기서 id column은 값이 auto_increment로 되어 있기 때문에, 입력해주지 않아도 자동으로 증가하며 생성된다. )

* **SELECT * FROM *tableName* (이건 Read 부분이지만 맛보기로..)** : 해당 테이블의 모습이 출력.

<img width="450" alt="2018-08-31 5 30 37" src="https://user-images.githubusercontent.com/39458555/44901922-9a6c4100-ad43-11e8-8804-3333cabd1f07.png">

( 사진 출처 : 생활코딩 - https://opentutorials.org/course/3161/19539 )

-----------

##### SQL의 SELECT 구문 ( Read 부분 )

	♻︎ 구글링을 통해 필요한 건 찾아서 쓰자 ! (여기는 기본 설명만.) 
	 mysql select syntax 검색하면 수많은 자료들이 나옴.

* **SELECT * FROM *tableName*** : 모든 데이터를 화면에 출력하고 싶을 때

  <img width="400" alt="2018-08-31 5 42 42" src="https://user-images.githubusercontent.com/39458555/44902561-52e6b480-ad45-11e8-94cd-dd777e6cff92.png">

* **SELECT *column lists* FROM *tableName*** : 원하는 column들만 선택해서 출력

  <img width="450" alt="2018-08-31 5 47 49" src="https://user-images.githubusercontent.com/39458555/44902851-02238b80-ad46-11e8-959c-e41a524b1df0.png">

* **SELECT *[column lists]* FROM *tableName* <u>WHERE</u> author='egoing'**; 이라고 하면 아래와 같이 해당 column들과 author 값을 egoing으로 가지고 있는 데이터들만을 출력한다. 

  <img width="450" alt="2018-08-31 5 53 28" src="https://user-images.githubusercontent.com/39458555/44903173-cd640400-ad46-11e8-8413-c89fb9418057.png">

* **SELECT [*column lists*] FROM *tableName* WHERE author='egoing' <u>ORDER BY</u> *columnName* DESC(내림차순)/ASC(오름차순)** : 해당 column을 기준으로 내림차순/오름차순으로 정렬한다.

  <img width="450" alt="2018-08-31 6 03 15" src="https://user-images.githubusercontent.com/39458555/44903680-2d0edf00-ad48-11e8-9047-466eedda726e.png">

* 명령 끝에 **LIMIT *number*** 를 입력해주면 수많은 데이터들 중에 위에서부터 number 수 만큼의 데이터만을 출력한다. 

( 사진 출처 : 생활코딩 - https://opentutorials.org/course/3161/19540 )

-------

##### SQL의 Update 구문

