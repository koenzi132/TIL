# complexity

> 일반적으로 Time complexity(시간복잡도)와 Space complexity(공간복잡도) 두 가지가 있다.

★ **Complexity가 중요한 이유** :

	complexity는 우리의 코드를 더 잘 이해하게 하여 효율성을 개선시킨다.

**<u>내가 짠 코드가 어떠한 complexity를 갖는지 아는 것은 매우 중요하다.</u>**

--------------

* **Space complexity(공간복잡도)** : 얼마나 많은 메모리나 얼마나 많은 용량을 차지하고 있는가.

* **Time complexity(시간복잡도)** : 얼마나 오랜 시간동안 연산을 수행하는가.

--------

◎ **<u>Big-O notation</u>** : 대략적인 time complexity를 보여줌.

	(정확한 값이 아닌 근사값으로 표현.)	
	
	<img width="911" alt="2018-08-24 4 40 16" src="https://user-images.githubusercontent.com/39458555/44571700-79907280-a7bc-11e8-8e91-295d0ca1a2cd.png">

* constant가 time complexity가 가장 작으므로 run-time이 가장 짧음. (Good!!)
* exponential 쪽으로 갈 수록 time complexity가 커져 run-time이 증가. (Bad :( !!)

> * **constant** :  <u>Array lookup</u>(알고 있는 index를 가지고 접근하는 것), <u>Hash table insertion</u>(object에 key/value 추가하는 것 같은)과 같은 경우.
> * **logarithmic** : <u>Binary search</u> (반으로 나눠서 결과 보고, 원하는 결과가 아닐 경우 또 반으로 나눠서 결과를 보고... 하는 식의..)같은 경우. -> log(n) 만큼의 복잡도를 가짐.
> * **linear** : Printing the elements in an array. (for-loop을 한 번 돌려 모든 element를 한 번씩 탐색하는 경우.)
> * **quadratic** : constant time operation inside two nested for-loops. (for-loop 안에 for-loop을 한 번 더 돌리는 것과 같은 경우. 중첩 for문.)
> * **exponential** : 상수의 n 제곱. 주로 password와 같은 경우에서 exponential하게 만듦으로써, password를 알아내기 힘들게 하는 목적으로 사용되기도 한다. (복잡하게 만들수록 password를 알아내기 힘들어지니까.)

----------

Complexity Cheat Sheet : http://bigocheatsheet.com/