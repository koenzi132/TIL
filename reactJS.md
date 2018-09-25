

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

* ReactDOM의 **<u>render</u>**는 기본적으로 두 개의 prarameter를 갖는다.

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

* JSX에서 class는 className으로 사용한다. 

  * class="A" (x) - > className="A" (o)
* React에서는, css 파일을 따로 만들어서 처리하는 경우가 별로 없고, Component 안에서  inline 방식으로 사용한다.
  * 이런 식으로 ... render 안에 object 변수로 선언해줌.
    <img width="300" alt="2018-09-16 3 01 43" src="https://user-images.githubusercontent.com/39458555/45593427-76566400-b9c1-11e8-9095-e30a150161c2.png">
    * (숫자값인 경우, px등과 같은 기호는 사용하지 않고 숫자만;
      문자값인 경우, "" 안에 넣어줄 것.)
    * css에서처럼 background-color로 표기하지 않고,
      backgroundColor와 같이 Camel case로 표기해서 사용.
      (컬러를 위의 ffde00와 같은 특정 값으로 해주고 싶을 때는 앞에 #를 붙여 쓴다. ""#ffde00"  /// 일반적으론 "white" 와 같이 사용.)
  * 이러한 css를 적용시키기 위해서는,
    return에 이렇게 적용하면 된다.  ( style={선언된 변수} )
    <img width="300" alt="2018-09-16 3 06 21" src="https://user-images.githubusercontent.com/39458555/45593476-52475280-b9c2-11e8-82b1-4fcfcf1ea3ff.png">

* 만약 각각에 다른 효과를 주고 싶으면 아래와 같이 사용하면 된다.

  <img width="350" alt="2018-09-16 3 16 13" src="https://user-images.githubusercontent.com/39458555/45593529-90914180-b9c3-11e8-89b9-8e4da8b76841.png">

  <img width="350" alt="2018-09-16 3 15 57" src="https://user-images.githubusercontent.com/39458555/45593538-9edf5d80-b9c3-11e8-8aca-4a30adfa3928.png">

---

##### 기본적인 Component 형식

* 보통 Component의 경우 변수 선언시 **<u>맨 앞글자를 대문자</u>**로 표기한다.

<img width="350" alt="2018-09-16 2 50 25" src="https://user-images.githubusercontent.com/39458555/45593355-e2d06380-b9bf-11e8-81b9-4f0cb8444136.png">

* children은 해당 this의 자식을 소환할 때. (ex - div 안의 텍스트, div 안의 div ...)

---

##### Virtual DOM에 뿌리는 방법 ( 리엑트DOM )

<img width="350" alt="2018-09-16 2 47 14" src="https://user-images.githubusercontent.com/39458555/45593339-6ccbfc80-b9bf-11e8-9002-bafcc01ac731.png">

---

##### JSX 문법에서 주석 처리 하는 법

* {} 안에 /* */ 를 이용해 주석처리를 한다.

  (ex - {/*word */})  

---

* **getInitialState**  : 컴포넌트가 실행되기 전 초기 상태를 나타냄.

![2018-09-25 1 48 31](https://user-images.githubusercontent.com/39458555/45993433-ed7aaf00-c0c9-11e8-9c89-d8a6cd7953b7.png)

---

* JSX event 설정 방법

![2018-09-25 3 37 32](https://user-images.githubusercontent.com/39458555/45996946-fa52cf00-c0d8-11e8-8f64-70113ba2019c.png)

이런 식으로 해당 태그 안에 이벤트를 설정한다. render와 마찬가지로 countPlus, countMinus와 같은 함수를 설정 한 다음에. (함수의 인자(e라든지..)를 넣어주어야 함. 그래야 발생된 이벤트가 넘어옴.)

![2018-09-25 3 39 06](https://user-images.githubusercontent.com/39458555/45997003-2a01d700-c0d9-11e8-9ea7-10effd1a555f.png)

---

* **JSX에서 넘어온 이벤트 타입은 <u>Synthetic Event 타입</u>이다.**

  ![2018-09-25 4 28 59](https://user-images.githubusercontent.com/39458555/45999267-232a9280-c0e0-11e8-8497-9f1e40b61991.png)

  위의 예문의 if문을 살펴보면, 

  e.shiftKey 는 shift키를 누르고 해당 이벤트(마우스 클릭이나 키보드 동작 등)를 시행했을 때에 작동하게 하는 것이다. 

---

* **Component는 직접 리스닝을 할 수 없다.** 

![2018-09-25 4 40 48](https://user-images.githubusercontent.com/39458555/45999831-ca5bf980-c0e1-11e8-86c6-622b30f80006.png)

이런식으로 컴포넌트 안에 버튼을 만들고 그 버튼에 이벤트를 걸어줄 경우, 작동이 되지 않는다.

<u>컴포넌트는 DOM을 감싸고 있는 존재이기 때문</u>**(Dom wrapper)**. 

버튼을 감싸고 있는 존재일 뿐이라 DOM에 걸린 이벤트를 받을 순 없다. (이벤트를 리스닝 할 수 없다.)

이벤트를 받는건 DOM(여기선 button 태그)이다. 



**해결방법** : 컴포넌트 안에서 DOM element의 이벤트를 할당하는 것. <u>속성값으로 이벤트 핸들러를 설정해줘야 한다.</u>

 ![2018-09-25 4 48 51](https://user-images.githubusercontent.com/39458555/46000207-e8762980-c0e2-11e8-9d9d-b7bb2f1c6d6e.png)

![2018-09-25 4 52 55](https://user-images.githubusercontent.com/39458555/46000424-794d0500-c0e3-11e8-9d48-241327b23bd2.png)

이런식으로.



---

 