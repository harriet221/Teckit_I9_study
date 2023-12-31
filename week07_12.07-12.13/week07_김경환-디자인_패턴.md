# 디자인 패턴

## 디자인 패턴이란?

디자인 패턴은 소프트웨어 개발의 일반적인 문제에 대한 해결책입니다. 더 나아가 모든 프로그래밍 언어 및 업계의 개발자가 자주 직면하는 문제에 대한 해결책이기도 합니다.

디자인 패턴은 표준화된 라이브러리들이나 함수들을 코드에 복사해 사용하는 것처럼 패턴들을 붙여넣기식으로 사용할 수는 없습니다. 패턴은 재사용할 수 있는 코드 조각이 아니라 특정 문제를 해결하는 방식을 알려주는 가이드입니다. 우리는 패턴의 세부 개념들을 적용하여 각자의 프로그램에 맞는 해결책을 구현할 수 있습니다.

## 디자인 패턴을 사용해야 하는 이유

- 디자인 패턴은 소프트웨어 디자인의 일반적인 문제들에 대해 시도되고 검증된 해결책들을 모은 것입니다.

    - 패턴을 배우게 되면 객체 지향 디자인의 원칙들을 사용해 많은 종류의 문제를 해결하는 방법들을 배울 수 있습니다.

- 디자인 패턴은 팀원들이 더 효율적으로 의사소통하는데 사용할 수 있는 공통 언어를 정의합니다

## 디자인 패턴의 장점

- 코드의 가독성과 확장성 향상

- 추후의 유지보수 비용 감소

- 초보자들에 대한 개발의 진입장벽 완화
    - 코딩 업계의 전문간들이 남겨놓은 일종의 해결책이기 때문

- 이미 정립되어 있는 패턴을 사용함으로써 팀원들과의 정확하고 빠른 소통
    - 소통이 빨라지고 개발시간도 단축

## 디자인 패턴의 단점
일반적으로 패턴의 필요성은 개발자가 추상화 수준이 부족한 프로그래밍 언어나 기술을 선택했을 때 발생합니다. 이 경우 패턴은 효과적이지만 일시적이고 복잡한 해결책을 제시할 수 있습니다.

예를 들어 Strategy 패턴의 경우 대부분은 최신 프로그래밍 언어에서 제공하는 람다 함수로 구현이 가능합니다.

또한 패턴을 갓 배운 초보자들이 프로젝트의 맥락을 무시하고 패턴을 적용시키려다 오히려 비효율적인 결과를 야기할 수 있습니다.

## GoF 디자인 패턴

GoF(Gang of Four) 디자인 패턴이란 에릭 감마, 존 블리시디스, 랄프 존슨, 리처드 헬름이라는 네 명의 개발자가 출간한 책에 나오는 23가지의 패턴입니다.

생성 패턴, 구조 패턴, 행위 패턴로 분류됩니다.

<img src="https://i.imgur.com/rV1kNYK.png" width="900">

### 생성 패턴

생성 패턴은 객체가 생성되는 방식에 독립적인 시스템을 만들어줍니다.

- 여러 상황에 맞는 객체 생성 매커니즘을 제공

- 코드를 유연하고 재사용 가능하게 유지

### 구조 패턴

구조 패턴은 시스템의 각 부분을 서로 독립적으로 변경하게 해줍니다.

- 유연성과 확장성 유지

- 큰 시스템을 구축할 때 여러 클래스를 구성하고 결합하는 방법에 중점

### 행동 패턴

행동 패턴은 서로 다른 객체가 서로 통신하는 방식입니다.

- 객체와 클래스가 서로 어떻게 통신하고 동작해야 하는지에 대한 지침 제공

<sub>https://refactoring.guru/ko, https://www.youtube.com/watch?v=Pzy_MPfGixg&ab_channel=%EB%85%B8%EB%A7%88%EB%93%9C%EC%BD%94%EB%8D%94NomadCoders, https://www.youtube.com/watch?v=An7kqZ5D7j8&ab_channel=GISDEVELOPER, https://www.youtube.com/watch?v=8wm2WQhKzsM&ab_channel=%EC%98%A4%EB%8A%98%EC%BD%94%EB%94%A9</sub>
