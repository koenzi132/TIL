## 리액트 네이티브 인풋박스 클리어 방법

<img width="612" alt="2018-11-28 11 41 04" src="https://user-images.githubusercontent.com/39458555/49125289-e7d85a00-f302-11e8-940b-e555107d7318.png">

위에 나와 있는 것처럼,

TextInput 태그 안에 **ref**를 만들어주고 이를 바꾸어주는 함수(clearText function과 같은)를 정의 후,

원하는 작업이 끝난 시점에 해당 함수를 호출하면 된다.