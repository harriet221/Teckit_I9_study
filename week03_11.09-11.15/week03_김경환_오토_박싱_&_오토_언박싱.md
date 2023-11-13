# 오토 박싱 & 오토 언박싱
## 박싱 & 언박싱
자바에서 변수형에는 기본형 타입과 참조형 타입이 있습니다. 박싱과 언박싱은 Wrapper 클래스를 통해 기본형 변수를 참조형 변수로 바꿔주는 기능입니다.

## Wrapper 클래스
자바의 Wrapper 클래스는 객체가 기본형 변수를 래핑하거나 포함하는 클래스입니다. 래퍼 클래스로 객체를 생성하면 객체 내에 기본형 변수값을 저장할 수 있습니다.

![오토박싱&언박싱](https://www.tcpschool.com/lectures/img_java_boxing_unboxing.png)

## Wrapper 클래스의 필요성
프로그램에 따라 기본 타입의 데이터를 객체로 바꿔줘야 하는 경우가 있습니다.

- ArrayList, HashMap, Scanner를 포함한 java.util 내의 패키지들은 객체만을 처리합니다.

- 멀티스레딩에서 동기화를 지원하려면 객체가 필요합니다.

## Wrapper 클래스의 장점

- 객체만 허용하는 컬렉션 프레임워크를 사용할 수 있습니다.

- 객체에서만 활용할 수 있었던 equals(), toString() 등의 여러 메소드를 호출할 수 있습니다.

## Wrapper 클래스 사용 예제

래퍼 클래스의 주요 용도는 기본 타입의 값을 박싱해서 포장 객체로 만드는 것이지만, 문자열을 기본 타입 값으로 변환할 때에도 사용됩니다. Void를 제외한 모든 래퍼 클래스에는 parse로 시작되는 정적 메서드가 있습니다. 이 메서드는 문자열을 매개 값으로 받아 기본 타입 값으로 변환합니다.

```java
public class Wrapper_Ex {
    public static void main(String[] args)  {
        String str = "10";
        String str2 = "10.5";
        String str3 = "true";
        
        byte b = Byte.parseByte(str);
        int i = Integer.parseInt(str);
        short s = Short.parseShort(str);
        long l = Long.parseLong(str);
        float f = Float.parseFloat(str2);
        double d = Double.parseDouble(str2);
        boolean bool = Boolean.parseBoolean(str3);
    }
}
```

## 오토 박싱 & 오토 언박싱
JDK(Java Development Kit) 1.5부터는 박싱과 언박싱이 필요한 상황에서 자바 컴파일러가 이를 자동으로 처리해줍니다. 이를 **오토 박싱과 오토 언박싱**이라고 합니다.

```java
// 오토 박싱
int i = 10;
Integer num = i;

// 오토 언박싱
Integer num2 = new Integer(10);
int j = num2;

// == 연산자를 활용할 경우에도 오토 박싱, 오토 언박싱이 적용되서 true 값을 반환합니다.
System.out.println(i == num); // true
```
<sup>new Integer()를 사용한 선언 방식은 JDK 9 이후로 비권장됩니다.</sup>
## 오토 박싱과 오토 언박싱의 성능
편의성을 위해 오토 박싱과 오토 언박싱이 제공되고 있지만, 내부적으로 추가 연산 작업을 거치게 됩니다. 따라서, 오토 박싱 & 언박싱이 일어나지 않도록 동일한 타입의 연산을 지향해야 합니다.

### 오토 박싱 연산
```java
public static void main(String[] args) {
    long t = System.currentTimeMillis();
    Long sum = 0L;
    for (long i = 0; i < 1000000; i++) {
        sum += i;
    }
    System.out.println("실행 시간: " + (System.currentTimeMillis() - t) + " ms");
}

// 실행 시간 : 19 ms
```

### 동일 타입 연산
```java
public static void main(String[] args) {
    long t = System.currentTimeMillis();
    long sum = 0L;
    for (long i = 0; i < 1000000; i++) {
        sum += i;
    }
    System.out.println("실행 시간: " + (System.currentTimeMillis() - t) + " ms") ;
}

// 실행 시간 : 4 ms
```
<sub>참고 문헌 : https://gyoogle.dev/blog/computer-language/Java/Auto%20Boxing%20&%20Unboxing.html, https://coding-factory.tistory.com/547, https://www.geeksforgeeks.org/wrapper-classes-java/, https://www.tcpschool.com/java/java_api_wrapper, https://www.theiotacademy.co/blog/java-wrapper-classes/