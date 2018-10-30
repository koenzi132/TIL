

### Terminal Command

---



<img width="732" alt="2018-09-13 6 15 57" src="https://user-images.githubusercontent.com/39458555/45479369-4ae53680-b781-11e8-93ed-120134d7b3e0.png">

---

* git stash 
  * git에 commit하기 전의 수정된 파일들을 초기값으로 돌려놓는다. 
    (만약 add만 해 놓거나, add도 안해서 빨간 글씨로 뜨는 파일들은, git stash를 사용하면 원래 수정되기 전 파일로 돌아가니 주의할 것.)
* npm i -g mocha : mocha를 글로벌하게 설치. ( = npm install -g mocha )
  * 설치 후 테스트 할 때는, 다음 명령어를 -> mocha (test 폴더명) 

----

### git upstream 관리법

1. git remote -v : 현재 remote 경로를 확인할 수 있다.

2. git remote add upstream + (포크받기 전 원본 repository 주소) : upstream이라는 경로를 만들어줌(원본 마스터으로의 경로).

3. git pull upstream master : 마스터에서 업데이트 되거나 한 내용들을 내 local로 받아온다.

   (conflict(충돌)가 생기는 경우 VS code를 열어서 충돌된 부분 중 어떤 것을 사용할 것인가를 선택해준다.)

   (여기서 선택을 잘 해줘야 내가 작업하던 원본이 손상 안 됨!)

4. 변경된 내용들을 내 repository로 commit / push 해준다.

그럼 마스터에서 변경된 내용들을 나도 그대로 받아올 수 있다!