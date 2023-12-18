# 싱글톤 패턴(singleton)

<img src="https://i.imgur.com/8a6sTqK.png" width=500>

싱글톤 패턴은 **생성 패턴**에 속하는 디자인 패턴입니다. 싱글톤 패턴은 클래스에 인스턴스가 하나만 있도록 하면서 전역에 해당 인스턴스에 대한 접근을 제공합니다.

## 싱글톤 패턴을 사용해야 하는 이유

한 사무실에서 프린터를 사용해야 한다고 가정해봅니다. 이때 프린터를 사용하려는 사람들은 많지만 같은 사무실 내의 직원들이 프린터를 각각 한대씩 보유하고 사용하기보다는 한대의 프린터를 두고 모두가 공유하는 방식이 효율적일 수 있습니다. 싱글톤 패턴은 이런 상황에서 해결책을 제시합니다.

## 싱글톤 패턴의 장점

- ### 다른 모든 클래스에서 접근할 수 있습니다.

    - 싱글톤으로 구현한 인스턴스는 '전역'이므로, 다른 클래스의 인스턴스들이 데이터를 공유할 수 있습니다.

- ### 인스턴스가 하나만 생성됨이 보장됩니다.

    - 클래스마다 새로운 인스턴스를 생성하고 메모리를 할당 받는 대신 하나의 인스턴스를 생성하고 메모리를 할당 받음으로써 메모리 낭비를 방지합니다.

<img src="https://i.imgur.com/tgrTboc.png" width="600">

## 싱글톤 패턴의 단점

- ### 단일 책임 원칙을 위반합니다.

    - 싱글톤 패턴은 클래스의 작업을 처리하는 역할 뿐 아니라, 자신의 인스턴스에 대한 접근을 관리하는 역할도 해야 합니다.

- ### 개방 폐쇄 원칙을 위반할 수 있습니다.

    - 싱글톤 패턴을 사용하는 객체가 혼자 너무 많은 책임을 맡거나, 너무 많은 데이터를 공유하게 되면 모듈 간의 결합도가 높아집니다. 이 경우 개방 폐쇄 원칙에 위배됩니다.

- ### TDD 환경에서 사용하기 어렵습니다.

    - TDD에선 단위 테스트가 주로 진행되는데, 이는 서로 독립적이고 어떤 순서로든 실행할 수 있는 환경이기 때문에 미리 생성된 하나의 인스턴스를 기반으로 구현하는 싱글톤 패턴으로는 적용하기 어렵습니다.

- ### 멀티스레드 환경에선 동기화 문제가 발생할 수 있습니다.
    ```java
    public static Singleton getInstance(String value) {
        if (instance == null) {
            instance = new Singleton(value);
        }
        return instance;
    }
    ```
    - 위는 싱글톤의 생성메소드입니다. 다른 환경과 다르게 멀티스레드 환경에선 if문을 동시에 호출할 수 있습니다. 이 경우 하나의 인스턴스를 가지도록 설계된 싱글톤 패턴에서 두개 이상의 인스턴스를 가지게 될 수 있습니다.

## 구현 방법(Lazy Initialization)

싱글톤을 구현하는 방법은 다양합니다. 아래의 방법은 그 중 Lazy Initialization을 구현합니다.

1. 싱글톤 인스턴스의 저장을 위해 클래스에 private static 필드를 추가합니다.
```java
public final class Singleton {
    private static Singleton instance;
}
```
2. 싱글톤 인스턴스를 가져오기 위한 public static 메소드를 선언합니다
```java
public final class Singleton {
    private static Singleton instance;

    public Singleton(){}
}
```
3. static 메소드 내에 'Lazy Initialization'를 구현하고 생성자를 private으로 바꿔줍니다. 이를 통해 해당 메소드를 호출할 때 인스턴스가 없다면 생성하고, 있다면 기존의 인스턴스를 활용합니다.
```java
public final class Singleton {
    private static Singleton instance;

    private Singleton(){}

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

<sub>참고 문헌
- https://refactoring.guru/ko/design-patterns/singleton
- https://invincibletyphoon.tistory.com/12
- https://gyoogle.dev/blog/design-pattern/Singleton%20Pattern.html
- https://readystory.tistory.com/116
- https://devjeong.com/design%20pattern/DesignPattern-1.1.1/
</sub>