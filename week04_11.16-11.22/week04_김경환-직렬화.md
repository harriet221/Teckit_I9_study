# 직렬화(serialize)
직렬화란 자바 안에서 사용되는 Object나 Data를 다른 컴퓨터의 자바 시스템에서도 사용할 수 있도록 바이트 형태로 데이터를 변환하는 기술입니다. 그 반대의 개념인 역직렬화는 바이트로 변환된 데이터를 원래대로 자바 시스템의 Object 또는 Data로 변환하는 기술입니다.

## 직렬화의 조건

- 기본형 변수
  - 직렬화는 데이터를 바이트 형태로 변환합니다. 기본 자료형들의 경우 바이트가 정해져 있기 때문에 변환이 가능합니다.

-  참조형 변수
   - 참조형 변수의 크기는 가변적이고, 참조형 변수를 구성하는 자료형들의 종류와 수에 따라 객체의 크기가 다양하게 바뀔 수 있습니다. 이를 위해 참조형 변수의 경우 Serializable 인터페이스를 구현해야 합니다.

- Transient 선언
  - 객체 내의 데이터 중 직렬화에서 제외하고 싶은 부분이 있다면 Transient를 선언함으로 직렬화 대상에서 제외할 수 있습니다.

## 직렬화의 사용처
직렬화를 사용하면 메모리의 힙과 스택에만 상주하던 데이터들을 그대로 영속화할 수 있습니다. 영속화된 데이터이기 때문에 네트워크로도 전송이 가능하고 필요할 때 직렬화된 객체 데이터를 가져와서 역직렬화 후 바로 사용할 수도 있습니다. 이를 활용하면 다음과 같은 곳에 활용할 수 있습니다.

- 서블릿 세션 (Servlet Session)

- 캐시 (Cache)

- 자바 RMI(Remote Method Invocation)

## 직렬화의 장점

- 직렬화는 자바의 고유 기술인 만큼 자바 시스템에서 개발이 최적화되어 있습니다.

- 자바의 다양한 레퍼런스 타입에 대해 제약 없이 외부에 내보낼 수 있습니다.
   - 타 언어에서도 사용되는 기본형 타입이나 배열과는 달리 자바 내에서만 사용되는 객체형 데이터들은 외부에 보내기 위해 별도의 파싱이 필요합니다. 직렬화를 통해 이런 복잡한 작업들을 생략할 수 있습니다.

## 직렬화의 단점

- 용량이 큽니다
   - 순수한 객체 내 데이터 뿐 아니라 타입 정보나 클래스 메타 정보를 포함하기 때문에 Json과 비교할 시 두배 이상의 차이를 보입니다.

- 버그와 보안에 취약합니다.
  - 역직렬화는 언어의 기본 메커니즘을 우회하여 객체를 바로 생성합니다. 악의적인 코드를 역직렬화할 경우 프로그램 코드 전체가 공격 범위에 들어갈 수 있습니다.

<sub>참고 문헌 : https://ryan-han.com/post/java/serialization/, https://techblog.woowahan.com/2550/, https://techblog.woowahan.com/2551/, https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%A7%81%EB%A0%AC%ED%99%94Serializable-%EC%99%84%EB%B2%BD-%EB%A7%88%EC%8A%A4%ED%84%B0%ED%95%98%EA%B8%B0#%EC%9E%90%EB%B0%94_%EC%A7%81%EB%A0%AC%ED%99%94_%EC%9E%A5%EC%A0%90