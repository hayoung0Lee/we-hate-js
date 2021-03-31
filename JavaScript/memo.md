# 프로퍼티 어트리뷰트

- 내부 슬롯과 내부 매서드는 `[[]]`로 감싸진 것들로 ECMAScript를 따라서 구현되어있고, 실제 JavaScript엔진 내에서 동작하고 있지만 개발자가 사용할 수 있도록 외부에 공개되어 있지는 않다.
- 모든 객체는 `[[prototype]]`이라는 내부 슬롯을 가지고 있는데, 개발자가 이에 직접 접근 할 수는 없다. 즉, `object.[[prototype]]`과 같은 방식으로 접근할 수 없다. 하지만 내부 슬롯 `[[prototype]]`의 경우 `__proto__`를 통해서 간접적으로 접근해서 사용할 수 있다.

# 생성자 함수에 의한 객체 생성

- 생성자 함수를 사용하면 이것을 마치 객체(인스턴스)를 생성하는 클래스처럼 사용해서 프로퍼티 구조가 동일한 객체를 여러개 쉽게 생성할 수 있다.
- js에서는 클래스 기반처럼 생성자가 형식이 정해진게 아니라, 일반 함수처럼 생겼는데, new와 함께 쓰면 생성자 함수로 동작한다.
- 함수는 객체라 객체로 할수있는건 다 할수있다. 그런데 객체는 추가적으로 [[Call]], [[Construct]] 같은 내부 메서드와, [[Environment]], [[FormalParameters]]와 같은 내부 슬롯을 추가적으로 가지고 있다. JS engine은 [[Call]]을 가진 함수만 callable해서 호출이 가능하다. 모든함수는 [[Call]]을 가져서 호출할 수있는데, [[Construct]]는 있을수도 없을수도있다.
  - 화살표 함수는 [[Construct]] 를 가지지 않는다.
  - 함수 선언문, 함수 표현식, 클래스는 [[Construct]]를 가진다.
- new.target 을 통해서 이 값이 true면 생성자 함수로 호출되었는지 확인이 가능하다. 일반함수로 호출되면 new.target은 undefined이다.

# 함수와 일급객체

- `__proto__` 는 접근자 프로퍼티이다.
- 함수는 arugment, caller, lenth, name, prototype 프로퍼티를 가진다.
- 모든 객체는 [[Prototype]] 이라는 내부 슬롯을 가지고 이는 `__proto__`를 통해서 접근할 수 있다.

# 프로토 타입

- 함수 객체만이 소유하는 prototype프로퍼티는 생성자 함수가 생성할 인스턴스의 프로토타입을 가리킨다.
- `for ... in`: 객체의 프로퍼티 개수만큼 순회한다. ([[Enumerable]]값이 true인 것만) 심벌은 포함하지 않는다.
  - [for in, for of 차이](https://stackoverflow.com/questions/29285897/what-is-the-difference-between-for-in-and-for-of-statements#:~:text=The%20only%20difference%20between%20them,arrays%2C%20strings%2C%20and%20NodeLists.)

# 질문 리스트

- p 224: [[Enumerable]] , [[Configurable]]은 어떻게 사용되는지..? -> p227쪽에 답이 있다.
- p 227
  - enumerable이 false면 for ... in 문이나 Object.keys로 열거가 안된다.
  - writable이 false면 해당 프로퍼티의 [[Value]] 변경이 안된다
  - configurable이 false면 삭제가 안된다
  - value, writable, enumerable, configurable 네가지가 있다
- p 243
  - 밑에 예제 이해가 잘안된다
- p 258m hasOwnProperty `__proto__`가 잘 이해가 안됨
  - `__proto__` 는 Object.prototype의 접근자 프로퍼티이다.
  - P267읽어보기
- p270 다시 읽기
- P274 뭔소린지..? OrdinaryObjectCreate가 이해가 안된다.
- p286 다시한번 보기
- p291 이렇게 쓰는 경우가 있나?? constructor를 왜 없애는..?
- p297 예제 19-48 이해 안됨
- p316: script마다 쓰라는건지 말라는건지 모르겠음. 하지만 하고 별표 쳐놓은 문장 무슨 뜻인지 모르겠음
- p302: Object.create 로 생성해야하는 경우가 있나..?
- p304: 예제 19-57 이해 안됨
  ```javascript
  obj.hasOwnProperty("name");
  // Object.hasOwnproperty()
  ```
