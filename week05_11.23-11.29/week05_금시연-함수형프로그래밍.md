# 함수형 프로그래밍(Functional Programming)

프로그램을 순수 함수들의 조합으로 작성하는 방법이다.

객체 중심으로 프로그램을 설계하는 객체지향 프로그래밍과 다르게, 무엇을 할지를 정하는 함수 중심으로 결과를 만들어낸다.

순수 함수(Pure Functions)는 함수가 가진 인자 외에 다른 외부 상태에 영향을 받지 않는다.
항상 동일한 입력에 대해 동일한 결과를 출력하도록 되어있어, 변경이 가능한 데이터나 상태 대신 불변성과 독립성을 강조한다.

Haskell, Scala 등이 대표적인 함수형 프로그래밍 언어이다.

## 장점

- 함수의 동작부가 간결하여 객체지향 프로그래밍에 비해 코드의 이해도와 가독성이 좋다.
- 테스트가 쉽다.

## 단점

- 외부 데이터 혹은 내부 데이터의 상태를 조작할 수 없다.

## 특징

### 순수 함수와 불변성(Immutable)

외부의 상태에 동작을 의존하거나 영향을 끼치지 않는 함수를 순수 함수라고 하며, 함수형 프로그래밍에서는 이를 조합해 더 큰 기능을 구현한다.

변경 가능한 상태를 없애서 프로그램 동작을 단순하게 하고, 예측하기 쉽게 만들어 코드의 안정성과 신뢰성을 높인다.

### 고차 함수(Higher-Order Functions)

고차 함수는 함수를 인자로 다루거나 반환하는 함수로, 다른 함수를 조작하고 결합해 유연한 동작을 구현하는 데 쓰인다.

필요에 따라 함수를 변수에 할당하고 호출할 수 있으므로 함수를 데이터 다루듯이 다룰 수 있고, 코드의 재사용성과 추상화 수준을 높여준다.

### 재귀(Recursion)

함수형 프로그래밍에서는 for, while 같은 반복문 대신 재귀 함수를 통해 문제를 해결한다.

재귀로 하여금 루프 단계마다 갱신되는 반복 변수를 제거하여 코드를 간결하고 가독성 좋게 만들 수 있다.

## 예시

```jsx
var arr = [1, 2, 3, 4, 5];
var condition = function(x) { return x % 2 === 0; }
var ex = function(array) {
  return array.filter(condition);
};
ex(arr); // [2, 4]
```

위 예제는 순수함수가 아니다. `ex` 메서드에서 인자로 들어오지 않은 `condition`을 사용했기 때문이다.

```jsx
var ex = function(array, cond) {
  return array.filter(cond);
};
ex(arr, condition);
```

순수함수로 고친 코드이다. 순수함수로 만들면 에러를 추적하는 것이 쉬워진다.

에러가 발생했을 때, 인자에 문제가 있거나 혹은 함수 내부에 문제가 있거나 둘 중 하나이기 때문이다.

## Java에서의 함수형 프로그래밍

Java 8부터 Java에서도 함수형 프로그래밍이 가능해졌다.

Java에서 활용할 수 있는 함수형 프로그래밍은 다음과 같다.

- 람다식
- Stream API
- 함수형 인터페이스

---

> 참고 자료
</br>[Inflearn | [INFCON Tech Series #3] 한눈에 보는 객체지향 프로그래밍 & 함수형 프로그래밍](https://www.inflearn.com/pages/infcon-2023-tech-oopfp)
</br>[Github | gyoogle/tech-interview-for-developer/Computer Science/Software Engineering/Fuctional Programming.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Software%20Engineering/Fuctional%20Programming.md)
