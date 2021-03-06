# **HTTP란?**

HyperText  Transfer Protocol의 약자로  인터넷 상에서 데이터를 주고 받기 위한 서버/클라이언트 모델을 따르는 프로토콜. 애플리케이션 레벨의 프로토콜로 TCP/IP 위에서 작동한다.

HTTP는 어느 종류의 데이터든지 전송할 수 있도록 설계되어있다. HTML 뿐만아니라 이미지, 동영상, 오디오, 텍스트 문서 등 종류를 가리지 않는다.

이름 그대로 하이퍼텍스트를 기반으로 데이터를 전송하겠다는 말이다. 간단히 말하면 링크기반으로 데이터에 접속하겠다는 의미이다.



## **작동방식**

HTTP는 서버/클라이언트 모델 방식에 따르며 클라이언트 요청(request)를 보내면 서버는 요청을 처리해 응답(response)한다.

<img width="407" alt="2018-08-28 9 16 15" src="https://user-images.githubusercontent.com/39458555/44722312-a66bbf00-ab07-11e8-8a96-4e204c0db15a.png">

1. **<u>클라이언트</u>** :서버에 요청하는 클라이언트 소프트웨어가 설치된 컴퓨터. chrome, ie 등 클라이언트 소프트웨어를 이용한다. 클라이언트는 URL을 이용해서 접속하고, 데이터를 요청할 수 있다.

2. **<u>서버</u>**: 클라이언트의 요청을 받아서, 요청을 해석하고 응답을 하는 소프트웨어가 설치된 컴퓨터. Apache, IIS 등. 서버소프트웨어다.



웹서버는 보통 표준포트인 80번 포트를 사용한다.

**Connectless & Stateless**

HTTP는 Connectless 방식으로 작동한다. 서버에 연결하고 ,요청에서 응답을 받으면 연결을 끊어버린다. 기본적으로 자원 하나에 대해서 하나의 연결을 만든다.

이런 작동 방식은 다음과 같은 장점과 단점을 만든다.



● 장점: 불특정 다수를 대상으로 하는 서비스에 적합한 방식이다. 수십만명이 웹 서비스를 사용하더라도 접속유지는 최소한으로 할 수 있기 때문에, 더 많은 유저의 요청을 처리 할 수 있다.

● 단점: 연결을 끊어버리기 때문에, 클라이언트의 이전 상태를 알 수 없다. 이러한 HTTP특성을 **stateless** 라 한다. Connectless로부터 특징이라 할 수 있으며 클라이언트의 이전 상태 정보를 알 수 없다. 이를 해결하기 위해 HTTP는 **Cookie**를 이용하여 문제를 해결하고 있다.



Cookie는 클라이언트와 서버의 상태 정보를 담고 있는 정보의 조각아다. 로그인을 예를 들자면, 클라이언트가 로그인에 성공하면, 서버는 로그인 정보를 자신의 데이터베이스에 저장하고 동일한 값 Cookie형태로 클라이언트에 보낸다. 클라이언트는 다음번 요청 때 Cookie를 서버에 보내며 서버는 Cookie값으로 자신의 데이터베이스를 조회해 로그인 여부를 확인 할 수 있다.



**URL**

웹 브라우저는 URL을 이용하여 자원의 위치를 찾는다. URL과 HTTP는 독립된 체계이다. HTTP는 전송 프로토콜이고, URL은 자원의 위치를 알려주기 위한 프로토콜이다. Uniform Resource Identifiers의 줄임말로 World Wide Web상에서 접근하고자하는 자원의 위치를 나타내기 위해서 사용한다. 자원은 문서,이미지,동영상,프로그램, 오디오 등 모든 것이 될 수 있다.

http://www.naver.com/search?dkajslf



1. http: 자원에 접근하기 위한 프로토콜

2. www.naver.com: 자원의 인터넷상의 위치. 도메인은 ip주소로 변환되므로 ip주소로 서버의 위치를 알 수 있음.

3. search?dkajslf: 요청한 자원의 이름

이렇게 프로토콜/위치/자원명으로 인터넷상에서 어디에 있던지 자원에 접근 할 수 있다.



**Method(메소드)**

메소드는 요청의 종류를 서버에게 알려주기 위해서 사용한다. 다음은 요청할 수 있는 메소드들이다.

● GET : 정보를 요청하기 위해서 사용한다.(SELECT)

● POST : 정보를 밀어넣기 위해서 사용한다.(INSERT)

● PUT : 정보를 업데이트하기 위해 사용한다.(UPDATE)

● DELETE : 정보를 삭제하기 위해서 사용한다.(DELETE)

● HEAD : (HTTP)헤더 정보만 요청한다. 해당 자원이 존재하는지 혹은 서버에 문제가 없는지 확인하기 위해서 사용한다.

● OPTIONS : 웹서버가 지원하는 메소드의 종류를 요청한다.

● TRACE : 클라이언트의 요청을 그대로 반환한다.

보통은 웹 서비스들은 GET과 POST만을 이용해서 개발한다. DELETE나 PUT 등이 필요한 요청에도 GET과 POST를 사용한다. 예를 들어 게시판에서 특정 레코드를 삭제 할 때도 GET으로 표현한다.



[ 자료출처: http://message0412.tistory.com/entry/HTTP-프로토콜-알아보기1 ]