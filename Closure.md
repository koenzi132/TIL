# Closure(클로저)

```
외부함수의 변수에 접근 가능한 내부함수, 조금 더 포괄적으로는 함수 선언시 생성되는 유효 범위.
```

* Closure는 프로그래머가 창조적이고 인상적이며 간결한 프로그래밍을 할 수 있게 해준다. 

* 내부함수는 외부함수의 변수 뿐만 아니라 파라미터에도 접근할 수 있다. 단, 내부함수는 외부함수의 arguments 객체를 호출할 수는 없다.
* Closure는 외부함수가 리턴된 이후에도 외부함수의 변수에 접근할 수 있다.
  * 따라서 내부함수를 나중에 호출할 수 있다.

* Clousre의 scope chain [ 1 ☛ 2 ☛ 3 순으로 탐색]

<img width="500" alt="closure scope" src="https://user-images.githubusercontent.com/39458555/44327508-ce20ae80-a499-11e8-8ab0-88a7d0203637.png">



* **Closure을 남발할 시**에는 Garbage Collector에 의해 정리되어야 할 것들이 메모리 상에 남아 있게 되기 때문에 비효율적인 메모리 사용을 하게 된다. 



