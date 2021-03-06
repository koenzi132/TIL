# 단위 테스트, TDD, BDD의 차이점

------

본 글을 Jani Hartikainen님이 작성한 “What’s the difference between Unit Testing, TDD and BDD?”라는 제목의 원문을 한글로 번역한 자료로써, **Jason Ryu**님의 Medium Blog에서 가져온 자료입니다.

(링크- https://medium.com/@sryu99/%EB%8B%A8%EC%9C%84-%ED%85%8C%EC%8A%A4%ED%8A%B8-tdd-bdd%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90-3d25fab5ccb2)

(링크- <https://codeutopia.net/blog/2015/03/01/unit-testing-tdd-and-bdd/>)

------

자동화된 Javascript 테스트를 처음 접하기 시작할 때, 단위 테스트(Unit testing), TDD(Test-Driven Development), BDD(Behavior-Driven Development)라는 단어들에 대해 많은 사람들이 이야기하고 있음을 발견할 수 있다. 관련 내용들을 살펴보다보면 자연스럽게 다음과 같은 궁금증들을 갖게 된다. ‘이것들 중 어떤 것이 가장 좋은 접근방식일까?’, ‘이 모든 것들을 사용할 수 있을까?’ 등등…

많은 수의 Javascript 개발자들과 이와 관련된 이야기를 나누면서 위에 언급한 3가지 단어에 대해서 혼란스러워하는 것을 발견할 수 있었다. 이러한 잘못된 이해를 바로잡기 위해 단위 테스트, TDD 그리고 BDD에 대해 살펴보고자 한다.

### 단위 테스트(Unit testing)

단위 테스트는 일반적으로 모듈이나 객체를 구성하는 단일함수 정도의 크기에 해당하는 코드 단위에 집중한다. 단일 함수에 대한 구체적인 테스트는 테스트 자체를 단순화하고 빠르게 작성하여 수행해 볼 수 있다는 장점을 갖는다. 이를 통해 많은 수의 단위 테스트들을 빠르게 만들 수 있고 보다 많은 버그를 발견하여 잡아 낼 수 있다. 특히 단위 테스트는 코드를 변경하는 경우 많은 도움을 준다. 구현된 코드에 대한 단위 테스트들을 갖고 있다면 변경과 상관없는 구현코드들이 이상없이 동작할 수 있다는 신뢰를 갖고 마음 편하게 코드를 수정할 수 있다.

단위 테스트는 네트워크 접근이나 DB 접근과 같은 의존성으로 부터 격리되어야 한다. 의존성들을 적절히 통제하여 테스트와 상관없는 임의의 것들로 교체하기 위한 다양한 도구들을 활용함으로써 실제 기능구동을 위해 필요로 하는 많은 사전 세팅 작업없이 모든 시나리오에 대한 테스트를 수행해 볼 수 있다. 하나의 테스트를 위해 전체 DB와 관련된 세팅 작업을 해야하는 상황을 떠올려본다면 … 생각만으로도 끔찍하다.

일반적으로 단위 테스트 작성과 관련하여 오해하고 있는 부분 중 단위 테스트가 반드시 특정 형식으로 작성되어야 한다고 생각하는 것이다. 소위 “xUnit style”이라고 불리는 형태로 작성하는 것이 일반적인데, 아래의 예제가 Mocha를 활용하여 “xUnit style” 형태로 작성한 테스트 코드이다.

```
suite('My test suite name', function() {
  setup(function() {
    //do setup before tests
  });
 
  teardown(function() {
    //clean up after tests
  });
 
  test('x should do y', function() {
    //test something
  });
});
```

하지만 위의 예는 특정한 툴에서 해당 형식으로 사용하는 하나의 예일 뿐, 단위 테스트를 반드시 특정 문법으로 작성해야 할 필요는 없다. 
단적인 예로 아래와 같이 일반 Javascript로도 Unit test를 작성할 수 있다.

```
//suite: User
 
//test: Name should start empty
var user = new User();
if(user.getName() !== '') {
  throw new Error('User name should start as empty');
}
 
//test: Password should be hashed
var user = new user();
user.setPassword('hello');
if(user.getPassword() != bcrypt('hello')) {
  throw new Error('User password should be hashed with bcrypt');
}
```

단위 테스트의 기본 조각들은 각각 하나의 행동에 대해서만 테스트 수행하고, 서로에 대해 독립적이어야 한다. 위와 같이 단순한 형태로 단위 테스트 코드를 작성할 수 있지만, Mocha, Jasmine과 같은 단위 테스트 지원도구들을 활용하여 보다 쉽게 테스트 코드를 작성할 수 있고, 테스트 실패에 대해 무엇이 잘못되었는가를 확인할 수 있는 상세 결과 출력과 같은 유용한 기능들의 도움도 받을 수 있다.

자동화 테스트를 단위 테스트만으로 오해하는 사람들이 있는데 이는 잘못된 생각이다. 다양한 종류의 자동화 테스트가 있고 각각은 그들만의 목적이 존재한다.

다음은 가장 일반적인 3가지 유형의 자동화 테스트들이다.

- **단위 테스트(Unit tests)**: 단일 객체 또는 함수 단위의 코드에 대한 테스트로, 각각의 테스트는 독립적으로 수행된다.
- **통합 테스트(Integration tests)**: 테스트 환경에서 데이터베이스에 대한 접근 코드를 테스트하는 것과 같이 여러 기능을 함께 테스트한다.
- **인수 테스트(Acceptance tests/Functional tests)**: 전체 Application에 대해 자동화 테스트를 수행하는 것으로 예를 들면 Selenium같은 툴로 웹브라우저를 자동으로 실행하여 전체 시스템에 대해 자동화 테스트를 수행하는 것을 의미한다.

단위 테스트를 작성하는 것이 쉽지 않다면, 수행하려는 테스트 레벨이 단위 테스트가 아닐 수도 있다. 통합 테스트와 인수 테스트는 더 복잡하고 느리게 수행되고, 단위 테스트보다 유지보수하기 어렵기 때문에 문제가 있는 경우 적절한 유형의 테스트를 작성해야 한다.

Javascript 코드에 대한 단위테스트 작성 팁이 궁금하다면 다음 링크([my JavaScript unit testing guide](https://codeutopia.net/h/subscribe/))에서 확인해 볼 수 있다.

### TDD

TDD(Test-Driven Development)는 언제 테스트를 작성하고 수행해야 하는지에 대한 절차이다. TDD를 수행하면 테스트 커버리지를 크게 높일 수 있다. 테스트 커버리지는 구현 코드에 대해 자동으로 테스트 되어지는 코드의 비율을 의미하므로 수치가 높을 수록 좋은 것이다. 테스트에 존재하는 버그는 추적이 어려운 특성이 있는데, TDD를 통해 테스트에 버그가 존재할 가능성을 줄여나갈 수 있다.

TDD는 다음의 절차로 구성된다.

1. 테스트 코드를 작성한다.
2. 작성한 테스트 코드와 기존에 작성된 다른 테스트들을 수행한다. 이 시점에서 새로 추가된 테스트 코드는 실패할 것이다. 만일 실패하지 않는다면 올바른 것을 테스트하고 있지 않은 것이므로 그 안에 버그가 있는 것이다.
3. 실패한 테스트를 성공시키기 위한 최소한의 코드를 구현부에 작성한다.
4. 실패한 테스트가 성공하는지 확인하기 위해 테스트를 재수행한다.
5. 필요에 따라 작성한 코드를 리펙토링한다.
6. 1번 부터 다시 반복한다.

이러한 절차를 배워나가기 위해 많은 노력이 필요하지만, 이 과정을 통해 많은 것을 얻을 수 있다. TDD로 진행된 프로젝트들의 코드 커버리지는 일반적으로 90~100%의 수치를 나타내는데, 이는 작성된 코드를 유지보수하거나 새로운 기능을 추가하는데 이점을 갖는다. 왜냐하면 많은 수의 테스트 코드들을 통해 다른 기능들이 깨지지 않은 상태로 변경작업을 진행할 수 있다는 신뢰를 얻을 수 있기 때문이다.

TDD 적용을 위해 반드시 “xUnit style”의 테스트 지원 툴들을 이용해야만 한다고 생각하는 사람들도 있지만 반드시 그런 것은 아니다. TDD는 단위 테스트 뿐만 아니라 다른 테스트 유형에도 적용할 수 있다. 또한 적용 시 반드시 특정한 툴을 사용하고 정해진 문법을 써야하는 것도 아니다.

TDD와 관련하여 많은 개발자들이 가장 어렵게 생각하는 것은 구현 코드 작성전에 테스트 코드를 먼저 작성한다는 점이다. 다음의 링크([5 step method to make TDD easy](https://codeutopia.net/blog/2016/10/10/5-step-method-to-make-test-driven-development-and-unit-testing-easy/))를 통해 TDD를 쉽게 적용하기 위한 5가지 방법에 대해 참고하는 것이 도움이 될 것이다.

### BDD

BDD(Behavior-Driven Development)는 가장 혼란스러울 수 있는 요소이다. BDD는 자동화 테스트를 적용 시 좋은 테스트를 작성하는 베스트 프랙티스 중 하나이다. BDD는 앞서 언급한 TDD와 단위 테스트와 함께 사용할 수 있고 실제로 그렇게 사용해야 한다.

BDD가 다루는 핵심 사항 중 하나는 단위 테스트의 세부 구현이다. 열악한 단위 테스트의 일반적인 문제는 단위 테스트가 테스트 대상 기능의 구현 형태에 너무 많은 영향을 받는다는 점이다. 즉, 테스트 대상 기능이 입출력 값의 변화없이 내부 구조만 변경되는 상황에서도 불필요하게 테스트 코드를 수정해야만 하는 상황을 야기하여 구현 코드 변경에 부담을 주게 된다.

BDD는 위의 문제 해결을 위한 테스트 작성 방식을 다음과 같이 제시한다. 
**“구현(Implementation)을 테스트하는 것이 아니라, 동작(Behavior)을 테스트하는 것이다.”**

다음의 예제를 통해 구현에 대해 생각할 때와 동작에 대해 생각할 때의 차이를 살펴보자.

```
suite('Counter', function() {
  test('tick increases count to 1', function() {
    var counter = new Counter();
 
    counter.tick();
 
    assert.equal(counter.count, 1);
  });
});
```

위 내용은 임의의 Counter객체에 대한 단위 테스트이다. tick 호출 시 Counter객체의 count값이 1이 되는 것을 테스트하는 것인데, 잘 작성되었다고 생각할 수 있지만 다음과 같은 문제가 있다. 위 테스트는 count가 0부터 시작한다는 것에 의존성을 같는다. 즉, 다음의 두 가지 내용에 의존성을 갖고 있는 것이다.

1. count값은 0부터 시작한다.
2. tick() 호출 시 1씩 증가한다.

count값이 0부터 시작한다는 것은 tick() 함수의 동작과는 무관한 Counter객체의 세부 구현 내용이므로 tick() 테스트에 영향을 주어서는 안되는 것이다. 이렇게 테스트를 작성하게 되는 이유가 바로 동작이 아닌 구현에 대해 생각하기 때문이다.

BDD는 동작에 대해 테스트를 작성하도록 제시한다. ‘어떤 형태로 코드가 구현되었는가?’를 고민하는 대신, ‘동작에 대한 시나리오가 어떻게 흘러가는가?’에 초점을 맞추는 것이다. 일반적으로 BDD 형식의 테스트는 “무엇인가를 해야한다(it should do something)”의 형태로 작성한다. (예: counter가 똑딱거리면 count를 1씩 증가시켜야 한다.)

여기서 중요한 부분은 구현보다는 시나리오에 대해 생각하는 것이 더 나은 테스트를 설계할 수 있다는 점이다.

```
describe('Counter', function() {
  it('should increase count by 1 after calling tick', function() {
    var counter = new Counter();
    var expectedCount = counter.count + 1;
 
    counter.tick();
 
    assert.equal(counter.count, expectedCount);
  });
});
```

위 내용은 Mocha의 BDD 스타일 함수를 활용하여 작성한 테스트로, 이전 테스트의 세부 구현 관련 문제점을 제거하였다. counter가 0부터 시작해야 하는 의존성 대신 counter.count + 1의 형태로 비교하도록 처리하여 tick의 동작자체에 대한 테스트 측면에서 의미를 더했다.

요구사항은 수시로 변경된다. Counter가 0이 아닌 다른 값부터 시작하도록 요구사항이 변경된다고 상상해보자. 세부 구현에 초점을 둔 테스트였다면 해당 요구사항 변경을 반영하기 위해 테스트코드에 대한 변경이 수반되어야 한다. 하지만 BDD를 활용하면 그럴 필요가 없어진다.

### 결론

단위 테스트는 테스트의 대상이 무엇(what)인가를, TDD는 테스트코드의 작성 시점(when)을, BDD는 테스트코드를 작성하는 방법(how)을 알려준다. 단위테스트, TDD, BDD를 각각 개별적으로 활용할 수도 있지만, 최상의 결과를 위해 각각을 적절히 조합하여 서로를 보완하는 형태로 사용해야 한다.