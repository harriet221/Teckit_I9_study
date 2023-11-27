# 문자열 클래스
자바에서는 대표적인 문자열을 다루는 자료형 클래스로 **String, StringBuffer, StringBuilder**라는 3가지 자료형을 지원합니다. 연산이 많지 않을 때는 어떤 클래스를 사용하더라도 차이가 없지만 연산 횟수가 많아지거나 멀티쓰레드 환경에서 사용될 경우 각각의 특징에 맞는 적절한 클래스를 사용하는 것이 중요합니다.

# 불변과 가변

## String : 불변

자바에서 String 객체의 값은 변경할 수 없습니다. 

한번 할당된 공간이 변하지 않는다고 해서 '불변 자료형'이라고도 불립니다. 그래서 초기 공간과 다른 값에 대한 연산에서 많은 시간과 자원을 사용하게 된다는 특징이 있습니다.

String 객체 내의 내부 구성 요소를 보면 다음과 같습니다.

<img src="https://i.imgur.com/PXG7dYJ.png" width="750"><br>

인스턴스 생성 시 생성자의 매개변수로 입력 받는 문자열은 이 value 라는 인스턴스 변수에 문자형 배열로 저장되게 됩니다. 이 value 라는 변수는 상수형이기 때문에 값을 바꾸지 못합니다.

<br>

아래의 예제 코드를 보면 변수 str이 참조하는 메모리의 "Hello"라는 값에 "World"라는 문자열을 더해서 String 객체 자체의 값을 업데이트 시킨 것으로 보일 수 있습니다.

```java
String str = "hello";
str = str + " world";

System.out.println(str); // hello world
```

<br>

하지만 아래의 그림과 같이 기존의 메모리는 두고 새로운 메모리에 값을 할당하는 식으로 작동합니다.

<img src="https://i.imgur.com/5mLUD2q.png">

<br>

이외에도 많이 사용하는 String의 메소드들 또한 수행 시 새로운 String 객체를 생성하여 리턴하기 때문에 메모리 누수가 발생합니다.

## StringBuffer, StringBuilder : 가변

StringBuffer와 StringBuilder는 객체의 공간이 부족해지는 경우 버퍼의 크기를 유연하게 늘려주어 **가변**적입니다.

두 클래스는 내부 Buffer에 문자열을 저장해두고 그 안에서 추가, 수정, 삭제 작업을 할 수 있도록 설계되어 있습니다. 이를 통해 .append(), .delete() 등의 메소드를 이용하여 동일 객체 내에서 문자열 크기를 변경하는 것이 가능합니다.


<img src="https://i.imgur.com/JQL3KoG.png">

따라서 값이 변경될 때마다 새롭게 객체를 만드는 String보다 훨씬 빠르기 때문에 추가, 수정, 삭제가 빈번할 경우 String 클래스가 아닌 StringBuffer나 StringBuilder를 사용하는 것이 효율적입니다.

# StringBuffer와 StringBuilder의 차이

StringBuffer와 StringBuilder는 둘 다 크기가 유연하게 변하는 가변적인 특성을 가지고 있으며, 제공하는 메서드와 사용법도 동일합니다.

하지만 멀티 쓰레드 환경 내 안정성에서 차이가 있습니다.

<img src="https://i.imgur.com/Zg55A9M.png" width="500">

<br>

두 클래스는 문법이나 배열구성도 모두 같지만, 동기화 지원 유무에서 차이를 가집니다. StringBuilder는 동기화를 지원하지 않는 반면, StringBuffer는 동기화를 지원하여 멀티쓰레드 환경에서도 안전하게 동작할 수 있습니다.

그 이유는 StringBuffer가 가지고 있는 synchronized 키워드 때문입니다.

자바에서 synchronized 키워드는 여러 개의 스레드가 한 개의 자원에 접근하려고 할 때, 현재 데이터를 사용하고 있는 스레드를 제외한 나머지 스레드들이 데이터에 접근할 수 없도록 막는 역할을 수행합니다.

```java
import java.util.*;

public class Main extends Thread{
  public static void main(String[] args) {
    StringBuffer stringBuffer = new StringBuffer();
    StringBuilder stringBuilder = new StringBuilder();

    new Thread(() -> {
        for(int i=0; i<10000; i++) {
            stringBuffer.append(1);
            stringBuilder.append(1);
        }
    }).start();

    new Thread(() -> {
        for(int i=0; i<10000; i++) {
            stringBuffer.append(1);
            stringBuilder.append(1);
        }
    }).start();

    new Thread(() -> {
        try {
            Thread.sleep(2000);

            System.out.println("StringBuffer.length: "+ stringBuffer.length()); // thread safe 함
            System.out.println("StringBuilder.length: "+ stringBuilder.length()); // thread unsafe 함
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }).start();
  }
}
```
```java
StringBuffer.length: 20000
StringBuilder.length: 19628
```

StringBuilder의 값이 더 작은 것을 볼 수 있습니다. 이는 복수의 쓰레드가 StringBuilder에 append()를 동시에 수행하는 상황에서 발생하는 결과입니다.


synchronized 키워드가 적용된 StringBuffer의 경우 복수의 쓰레드가 동시에 append()를 수행하는 것을 막아줌으로써 멀티쓰레드 환경에서의 안정성을 보장할 수 있습니다.

# 순수 성능 비교

문자열을 구성할 때 String과 StringBuffer, StringBuilder 간의 성능 차이를 확인하기 위해 100000번의 반복 루프 연산을 수행시킨 후 시간을 재보았습니다.

```java
public class Main {
    public static void main(String[] args) {
        long startTime = System.currentTimeMillis();

        String a = "test";

        for (int i = 0; i < 100000; i++) {
            a += "concat";
        }

        long endTime = System.currentTimeMillis();

        long resultOfA = endTime - startTime;

        startTime = System.currentTimeMillis();

        StringBuffer b = new StringBuffer("test");

        for (int i = 0; i < 100000; i++) {
            b.append("concat");
        }

        endTime = System.currentTimeMillis();

        long resultOfB = endTime - startTime;

        startTime = System.currentTimeMillis();

        StringBuilder c = new StringBuilder("test");
        for (int i = 0; i < 100000; i++) {
            c.append("concat");
        }

        endTime = System.currentTimeMillis();

        long resultOfC = endTime - startTime;

        System.out.println("String 연산 결과 : " + resultOfA); // String 연산 결과 : 4886
        
        System.out.println("StringBuffer 연산 결과 : " + resultOfB); // StringBuffer 연산 결과 : 4


        System.out.println("StringBuilder 연산 결과 : " + resultOfC); // StringBuilder 연산 결과 : 3
    }
}
```

StringBuilder, StringBuffer, String 순의 연산 속도를 보입니다. 이와 같이 String 개체를 사용하는 것은 불변성으로 인해 StringBuffer, StringBuilder와는 확연한 차이가 납니다. 또한 StringBuilder의 경우 동기화를 신경 쓸 필요가 없기 때문에 StringBuffer보다 빠르다는 것을 확인할 수 있습니다.