# TDD란?

테스트 주도 개발이라고 하며, 반복 테스트를 이용한 소프트웨어 방법론이다.

작은 단위의 테스트 케이스를 작성하고 이를 통과하는 코드를 추가하는 단계를 반복하여 구현한다.

## TDD 절차

<img width="50%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/17fe0192-1f1d-4d3e-b687-981bb4da6e96">

- RED 단계에서는 실패하는 테스트 코드를 먼저 작성한다.
- GREEN 단계에서는 테스트 코드를 성공시키기 위한 실제 코드를 작성한다.
- BLUE 단계에서는 중복 코드 제거, 일반화 등의 리팩토링을 수행한다.

실패하는 테스트 코드를 작성할 때까지 실제 코드를 작성하지 않는 것과, 실패하는 테스트 코드를 통과할 정도의 최소 실제 코드를 작성하는 것이 중요하다.

이를 통해 실제 코드에 대해 기대되는 바를 보다 명확하게 정의하여 불필요한 설계를 피할 수 있고, 정확한 요구사항에 집중할 수 있다.

# 일반적인 개발 방식 vs TDD 개발 방식

## 일반적인 개발 방식

보통의 개발 방식은 ‘요구사항 분석 → 설계 → 개발 → 테스트 → 배포’ 형태의 개발 주기를 가진다.

![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/c3408d0f-9908-4ac1-aab9-ef33b9c1f47c)

이러한 방식은 소프트웨어 개발을 느리게 하는 위험이 존재한다.

그 이유는 다음과 같다.

- 소비자의 요구사항이 처음부터 명확하지 않을 수 있다.
- 따라서 처음부터 완벽한 설계가 어렵다.
- 자체 버그 검출 능력이 저하되거나 소스코드의 품질 저하될 수 있다.
- 자체 테스트 비용이 증가할 수 있다.

보통 프로젝트의 초기 설계부터 완벽할 수 없고, 고객의 요구사항 또는 디자인 오류 등 많은 요인으로 인해 재설계하여 점진적으로 완벽한 설계를 해나간다.

하지만 이러한 재설계로 인해 개발자는 코드를 삽입, 수정, 삭제하는 과정에서 불필요한 코드를 남기거나 중복처리가 될 가능성이 크다.

결론적으로 이러한 코드들은 재사용과 관리가 어려워 유지보수를 힘들게 만든다.

## TDD 개발 방식

TDD와 일반 개방 방식과의 가장 큰 차이점은 테스트 코드를 작성한 뒤에 실제 코드를 작성한다는 점이다.

![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/7cad833b-54d5-457e-a137-17b8f199632f)

디자인(설계) 단계에서 프로그래밍 목적을 반드시 미리 정의해야 하고, 테스트 코드를 미리 작성해야 한다.

테스트 코드를 작성하는 도중에 발생하는 예외(버그 및 수정사항)는 테스트 케이스에 추가하고 설계를 개선한다.

이후 테스트가 통과된 코드만을 코드 개발 단계에서 실제 코드로 작성한다.

이러한 단계가 반복적으로 진행되면서 자연스럽게 버그는 줄어들고 소스코드는 간결해진다.

또한 테스트 케이스를 작성하는 과정에서 설계가 개선되므로 재설계 시간이 절감된다.

# TDD의 장점과 단점

## 장점

1. 보다 튼튼한 객체 지향적인 코드 생산
2. 재설계 시간 단축
3. 디버깅 시간 단축
4. 테스트 문서 대체 가능
5. 추가 구현의 용이함

## 단점

1. 생산성 저하</br>
    TDD 방식의 개발 시간은 일반적인 개발 방식에 비해 대략 10~30% 정도 늘어난다.   </br> 
    처음부터 2개의 코드를 짜야하고 계속 테스트를 하면서 고쳐나가야 하기 때문이다.    </br>
    SI 프로젝트에서는 소프트웨어의 품질보다는 납기일 준수가 훨씬 중요하기 때문에 TDD 방식을 잘 사용하지 않는다.

</br>

> 참고 자료</br>
[Tistory | 개발개발 울었다 - [기술면접] TDD(Test-Driven-Development) 방법론에 대해서](https://wooaoe.tistory.com/33)</br>
[Tistory | Inpa Dev 👨‍💻 - 🧪 TDD 방법론 (테스트 주도 개발) - 알기 쉽게 정리](https://inpa.tistory.com/entry/QA-%F0%9F%93%9A-TDD-%EB%B0%A9%EB%B2%95%EB%A1%A0-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%A3%BC%EB%8F%84-%EA%B0%9C%EB%B0%9C)
