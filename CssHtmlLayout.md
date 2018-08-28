# TIL

```
<CSS>
 - text-align: center / left / right ( 화면상의 텍스트 위치 )
 
 - 보통 body태그 안에 구간을 나눌 때 쓰는 태그들은..
 	: <div></div>
 	  <section></section> : 섹션 나누는..
 	  <header></header> : 헤더 역할 하는 것
 	  <nav></nav> : 네비게이션들
 	  <footer></footer> : 홈페이지 하단의 첨부내용 같은 거..
 	  <aside></aside> : 광고 같이 상대적으로 중요도가 낮은 것들을 넣음.
 
 - Layout
 [flex (flex를 사용하기 위해서는 parent 태그에 "display: flex" 라고 적용을 시켜줘야한다.)]
  display: flex;
  flex-direction: row / colum / row-reverse / colum-reverse
  flex-basis: OOpx;
  flex-shrink: 1 / 2 /... ( 사이즈를 n분해서 각각 해당 값만큼을 나누어감. )
  
 [parent 태그 안의 태그들을 수직으로 늘어놓는 방법]
 	parent 태그에 flex 태그를 적용한 다음 ( flex-direction: colum )를 적용
 [수평으로 늘어놓으려면]
 	parent 태그에 flex 태그를 적용 (기본적으로 flex-direction: row)가 적용됨.
 	
 [동일 class 내의 n번째 태그에만 css효과를 넣고 싶을 때]
 (class='item'일 경우)
  -> .item:nth-child(number) : number에 숫자를 넣어주면 그 숫자에 해당하는 번째의 태그	에 효과가 들어감.
```

<Holly Grail layout>

<img width="1398" alt="7-19-18hollygrail" src="https://user-images.githubusercontent.com/39458555/44572939-405a0180-a7c0-11e8-98ee-2b1d34585906.png">

