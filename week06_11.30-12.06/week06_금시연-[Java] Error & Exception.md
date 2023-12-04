# 개요

프로그램이 실행 중에 어떤 원인에 의해 오작동하거나 비정상적으로 종료되는 경우를 프로그램 오류라고 하고, 이는 Error와 Exception으로 구분할 수 있다.

Error는 시스템이 종료되어야 할 수준처럼 수습할 수 없는 심각한 문제를 의미하며, 개발자가 미리 예측하여 방지할 수 없다.

Exception은 개발자가 구현한 로직에서 발생한 실수나 사용자의 영향에 의해 발생하며, 미리 예측하여 방지할 수 있으므로 상황에 맞는 예외처리가 필요하다.

# Throwable 클래스

![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/3a14db6b-ed25-40e8-a41c-346ca38af742)

Throwable 클래스는 예외처리의 최상위 클래스로, Exception과 Error 클래스가 이 클래스를 상속받는다.

# Error 종류

- `StackOverflowError`: 호출의 깊이가 깊어지거나 재귀가 지속되어 stack overflow 발생 시 생기는 오류이다.
- `OutOfMemoryError`: JVM이 할당한 메모리의 부족으로 더 이상 객체를 할당할 수 없을 때 발생하는 오류이다. 이는 garbage collector에 의해 추가적인 메모리가 확보되지 못하는 상황이기도 하다.

# Exception 종류

## Checked Exception

예외처리가 필수이며, 처리하지 않으면 컴파일되지 않는다.

JVM 외부와 통신할 때 주로 쓰인다.

- RuntimeException 이외의 모든 예외
- `IOException`, `SQLException` 등이 있다.

## Unchecked Exception

컴파일 때 체크되지 않고 런타임 때 발생하는 예외이다.

- RuntimeException 하위의 모든 예외
- `NullPointerException`, `IndexOutOfBoundException` 등이 있다.

## 대표적인 Exception 클래스

- `NullPointerException`: Null 레퍼런스를 참조할 때 발생한다.
- `IndexOutOfBoundException`: 배열과 유사한 자료구조에서 범위를 벗어난 인덱스 번호를 사용할 때 발생한다.
- `FormatException`: 문자열, 숫자, 날짜 변환 시 잘못된 데이터 변환으로 발생한다.
- `ArithmeticException`: 숫자를 0으로 나눌 때 발생한다.
- `IllegalArgumentException`: 잘못된 인자 전달 시 발생한다.
- `IOException`: 입출력 동작 실패 또는 인터럽트 시 발생한다.

## 주요 Method

- `printStackTrace()`: 발생한 Exception의 출처를 메모리상에서 추적하여 결과를 알려준다. 발생한 위치를 정확히 출력해주므로 제일 많이 쓰인다.
- `getMessage()`: 한 줄로 요약된 메세지를 String으로 반환한다.
- `getStackTrace()`: printStackTrace()를 보완한 것으로, StackTraceElement[]라는 문자열 배열로 변경해서 출력하고 저장한다.

# Exception Handling

Java에서는 예외가 발생하면 Exception 객체를 생성한다.

예외를 처리하는 방법에는 크게 2가지가 있다.

1. 직접 try-catch문을 이용하여 예외에 대한 최종적인 책임을 지고 처리하는 방식
2. throws Exception을 이용하여 발생한 예외의 책임을 호출하는 쪽이 책임지도록 하는 방식

## try-catch로 예외 잡기

- try 블럭에는 예외가 발생할 수 있는 위험한 로직이 들어가고, catch 블럭에는 예외가 발생했을 때 수행할 로직이 들어간다.
- try 블럭을 수행하던 중에 예외가 발생하면 그 다음의 코드들은 실행되지 않으며 바로 catch 블럭으로 넘어간다.
- catch 블럭은 어떤 예외를 받는지에 따라 여러 개 쓸 수 있다.
- finally에는 예외 발생 여부와 관계없이 공통으로 실행하고자 하는 로직이 들어간다.
- 여러 catch 블럭 사용 시에는 Exception 클래스 계층 구조에서 자식 클래스에 해당하는 에러를 먼저 받는다.

## throws로 예외 던지기

예외가 발생했을 때 현재 메소드가 직접 처리하지 않고, 그 메소드를 호출한 곳에 예외의 발생 여부를 통보한다.

```java
public class ThrowsEx {
    public void call_A() throws Exception {
        call_B();
    }

    private void call_B() throws Exception {
        call_C();
    }

    private void call_C() throws Exception {
        System.out.println(1 / 0);
    }

    public static void main(String[] args) throws Exception {
        ThrowsEx test = new ThrowsEx();
        test.call_A();
    }
}
```

---

> 참고자료</br>
[Tistory | 최블랙의 개발로그 - [Java] Error와 Exception](https://choiblack.tistory.com/39)</br>
[Github | GimunLee/tech-refrigerator/Language/Java/Error&Exception.md](https://github.com/GimunLee/tech-refrigerator/blob/master/Language/JAVA/Error%20%26%20Exception.md#error--exception)
>
