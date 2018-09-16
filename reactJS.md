## React.js

* React.js는 User Interface를 만들기 위한 javascript library이다. ( Framework가 아님 )
* Facebook에서 개발한, UI(유저인터페이스)에 집중하는 Library.
* 자바스크립트와는 다르게 **<u>JSX문법</u>**을 많이 사용한다.
* React는 복잡한 상태변화를 잘 관리할 수 있게 해주는 상태시스템이다. (State Machine)
  * MVC Framework가 아님. MVC에서 V(view)를 담당한다 할 수 있음.
  * React는 가상 DOM을 이용해 DOM을 읽지 않고 갱신할 수 있는 강력한 렌더링 시스템을 가지고 있음.
* React는 **<u>UI library</u>**이고, **ReactDOM**은 <u>React를 웹사이트에 출력(render)하는 걸 도와주는 모델</u>이다. 
  - **ReactNative**는 모바일앱.

---



> <u>**Library (라이브러리)**와 **Framework (프래임워크)** ?</u>
>
> * 공통점 : 다른 사람의 도움을 받아 소프트웨어를 만든다. (다른 사람과 협력)
>
> * 차이점 : (생활코딩 egoing님의 견해) 
>   **Library**는 ∙∙∙ 내가 만들고자 하는 프로그램에 필요한 부품(?)들이 되는 소프트웨어들을 잘 정리정돈 해놓은, 재사용하기 쉽도록 되어있는 소프트웨어라고 할 수 있다. 내가 만들고 있는 프로그램에 필요한 부품을 가져오는 느낌. 
>   (대표적인 javascript library로는 jQuery가 있다. )
>
>   **Framework**는 ∙∙∙ 우리가 만들고자 하는 것이 있을 때, 그것이 무엇이냐에 따라서( 게임, 웹, 채팅 등 ) 그것을 만들고자 할 때 공통적으로 필요한 부분이 있을 것이고, 우리의 기획 의도에 따라 달라지는 부분이 존재하는데, 공통적인 부분을 framework이 만들어 놓고, 기능이나 개성에 따라 달라지는 것을 우리가 손보는 형식으로 작업할 때 사용한다. 우리가 만들고자 하는 것을 처음부터 끝까지 만들지 않도록 하는, 반제품과 같은 것이 framework이다. 

---

* React 작업환경 설정

  *  Node.js / NPM 설치해야 함.
  * babel, webpack, webpack-dev-server 설치해야 함.
    * (npm install -g babel webpack webpack-dev-server )
  * Nodes.js 프로젝트를 생성 (npm init) (원하는 폴더로 이동해서 할 것.)
    * npm init은 현재 위치에 package.json 파일을 생성한다. (json파일 안에 패키지 관리를 하기 위한 내용들이 모두 들어있음.)
      * 보통 package.json 파일을 설치한 뒤, 의존 패키지들을 설치한다. 
        (의존 패키지란, 패키지 파일을 이용하기 위해 필요한 기능을 가진 하위 패키지를 일컬음.)
  * 의존 패키지 및 플러그인 설치
    * npm install --save react react-dom
    * npm install -- save-dev babel-core babel-loader babel-preset-react babel-preset-es2015 webpack webpack-dev-server
      ( + react-hot-loader)

  (--save 는, 의존 패키지의 정보를 자동으로 package.json 파일에 적용하겠다는 것임. )

  (babel은 JSX문법을 javascript로 변환해서, 브라우저가 알아듣게 하는 역할을 함.)

---

### JSX를 공부해보자.

* **<u>render</u>**는 기본적으로 두 개의 prarameter를 갖는다.

  * ```react
    ReactDOM.render( 
    <h1> Hi React <h1>, ---> 보여주고픈 것 ( 첫 번째 parameter )
    document.body ); ---> 보여줄 위치 ( 두 번째 prarameter )
    ```

    * 결과 : html body에 'Hi React'가 뜸.

  * 위의 내용은 사실상 아래와 같음.

  * ```react
    ReactDOM.render( React.createElement(
    "hi",
    null,
    "Hi React"
    ),
    document.body
    );
    ```

##### 기본적인 Component 형식

<img width="450" alt="2018-09-16 2 45 03" src="https://user-images.githubusercontent.com/39458555/45593328-270f3400-b9bf-11e8-9f2e-125d759a61ee.png">

##### Virtual DOM에 뿌리는 방법 ( 리엑트DOM )

<img width="450" alt="2018-09-16 2 47 14" src="https://user-images.githubusercontent.com/39458555/45593339-6ccbfc80-b9bf-11e8-9002-bafcc01ac731.png">

