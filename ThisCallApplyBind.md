# Execution context

* **<u>Execution context</u>** 
  * 어떤 함수가 호출되면, 실행 컨텍스트(execution context)가 만들어짐.
    * call stack에 push (**<u>dev tool의 sources에서 함수 실행시 call stack에 표시되는 것들 하나하나가 execution context들임.</u>**)
    * 함수를 벗어나면 call stack에서 pop
  * scope 별로 생성
  * 담긴 것
    * scope 내 변수 및 함수 (Local, Global)
    * 전달 인자 (arguments)
    * 호출된 근원 (caller) (**<u>argument.callee.caller</u>**로 확인 가능)
    * **<u>this</u>**

---

# this

* **<u>this</u>** 

  * 모든 함수 scope 내에서 자동으로 설정되는 특수한 식별자
  * execution context의 구성 요소 중 하나로, 함수가 실행되는 동안 이용할 수 있다.

* **5 patterns of Binding 'this'**

  * <u>'this'는 함수가 어떻게 호출되는 지에 따라 달라진다.</u>★

  <img width="1093" alt="this" src="https://user-images.githubusercontent.com/39458555/44331632-05488d00-a4a5-11e8-8dc3-14d78c1eda72.png">

  • <u>**Global** ➢ 'this' = window</u>

  • <u>**Function 호출** ➢ 'this' = window</u>

  • <u>**Method 호출** (object의 key(method)의 value에 함수가 달려있는 경우) ➢ 'this' = 부모 object</u>

  • <u>**Construction mode** ( new 연산자로 생성된 function 영역의) ➢ 'this' = 새로 생성된 객체(instance)</u>

  ```
  function Car(name) {
      this.name = name;
  }
  var benz = new Car('benz'); //여기서 var benz의 benz(instance)가 this가 됨.
  benz.name // "benz"
  ```

  • <u>**call / apply 호출** ➢ 'this' = call / apply 의 첫 번째 인자로 명시된 객체</u>

---

# call & apply & bind

* call 과 apply 는 첫 번째 인자를 'this'로 갖는다.

* call 과 apply 의 차이는...

  * call 은 인자를 하나씩 쉼표로 나눠서 넣어줌.

  ```javascript
  [Function.prototype.call]
   - function.call(thisArg, arg1, arg2, ...)
  ex) add.call(obj, 2, 8, 4 ...)
  ```

  * apply 는 인자로 array를 가져옴.

  ```javascript
  [Function.prototype.apply]
   - function.apply(thisArg, [argsArray])
  ex) add.apply(obj, [2, 8, 4 ...])
  ```

* **arguments는 유사 배열이다.** 따라서 length는 존재하지만 array 관련 메소드들은 사용할 수 없기 때문에 call이나 apply를 사용해서 이용한다. 

  ```
  ex) Array.prototype.slice.call( arguments )
  ```

* **Bind (Function.prototype.bind)**

  * 인자로 넘겨준 객체와 연결(bind)된 새로운 함수를 반환.
  * callback 함수를 특정 객체와 연결하고 싶을 때 사용.

  ```
  fn.bind(thisArg[, arg1[, arg2[, ...]]])
  ```

  (실행하지 않는다. 'this'만 binding 해주고 끝.)

  ```
  ex)
  function foo() {
      return this;
  }
  var boundFoo = foo.bind({a:1});
  foo(); // this === window
  boundFoo(); // this === {a:1}
  ```

★**(주의) setTimeout에서 함수를 전달할 때, this를 설정하지 않은 경우, 일반적으로 window(전역객체)가 this가 된다. **

> ☛ 따라서 bind를 통해 this를 명시적으로 정해주어야 한다.

```
ex) setTimeout(b.printArea.bind(thisArg), 1000);
```

(setTimeout 문제를 해결할 때 bind를 주로 많이 사용한다.)

