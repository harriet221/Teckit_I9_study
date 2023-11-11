# Primitive type & Reference type
## 변수
변수란 데이터를 저장하기 위해 프로그램에 의해 이름을 할당받은 **메모리 공간**을 의미합니다. 자바에서 말하는 **데이터 타입**(자료형)은 변수에 적재할 데이터가 어떤 식으로 활용될 수 있는지 알려주는 키워드이기도 합니다.

변수에는 두가지 종류가 있습니다.
- 기본형 타입(Primitive Type)

- 참조형 타입(Reference Type)

## 기본형 타입(Primitive type)

자바에서는 총 8가지의 기본형 변수를 제공합니다.

## 기본형 타입의 특징

- 소문자로 시작된다.

- 변수의 선언과 동시에 메모리가 생성된다.

- 모든 값 타입은 메모리의 스택(stack)에 저장된다.

- 저장공간에 실제 자료 값을 가진다.

- 비객체 타입이 아니므로 null 값을 가질 수 없다. (기본값이 정해져 있다)


## 기본형 타입의 종류
자바의 기본형 변수들은 세가지 타입으로 분류할 수 있습니다.

### 정수형
|타입|메모리 크기|기본값|데이터의 표현 범위
|-|-|-|-
|byte|1 byte|0|-128 ~ 127
|short|2 byte|0|-32,768 ~ 32,767
|int(기본)|4 byte|0|-2E9 ~ 2E9 의 근삿값
|long|8 byte|0L| -9E18 ~ 9E18 의 근삿값

<sub>int와 long은 정해진 값이 있지만 이해하기 편하도록 지수를 통해 표현하였습니다.</sub>
- 자바의 정수를 표현하기 위한 자료형입니다. 주로 사용되는 자료형은 int, long이고 byte와 short는 잘 사용되지 않습니다.
- long 자료형을 사용할 경우 대입하는 숫자값이 int형의 표현범위 보다 높을 경우 값 뒤에 L을 붙여주어야합니다.
- 실수형
```java
int num = 10;

long longNum = 12345678912345L;
```
### 실수형
|타입|메모리 크기|기본값|데이터의 표현 범위
|-|-|-|-
|float|4 byte|0.0F|-3.4E38 ~ + 3.4E38 의 근삿값
|double(기본)|8 byte|0.0|-1.7E308 ~ + 1.7E308 의 근삿값
- 자바의 실수를 표현하기 위한 자료형입니다.
- long 자료형처럼 float 자료형도 float 변수에 값을 대입할 때 값 뒤에 f를 붙여주어야합니다.
```java
float floatNum = 1.23F;

double doubleNum = 1.23456789123456;
```
### 논리형

|타입|메모리 크기|기본값|데이터의 표현 범위
|-|-|-|-
|boolean|1 byte|false|true, false
- 참(true) 또는 거짓(false)의 값을 갖는 자료형입니다.
- if나 while문과 같은 조건문에 자주 활용됩니다.

```java
boolean bool = (2 > 1);             // true
boolean bool = (1 == 2);            // false
boolean bool = (3 % 2 == 1);        // true
boolean bool = ("3".equals("2"));   // false
```

### 문자형

|타입|메모리 크기|기본값|데이터의 표현 범위
|-|-|-|-
|char|2 byte|\u0000|0 ~ 65,535
- 한 개의 문자 값에 대한 자료형입니다.
- 사용 시 따옴표(')를 활용해 감싸주어야 합니다.
```java
char a1 = 'a';
```




## 참조형 타입(Reference type)
참조형 변수는 위의 8가지 자료형을 제외한 나머지를 말합니다. 자주 활용되는 String 또한 참조형 타입 중 클래스 타입에 속해있습니다.

## 참조형 타입의 특징
- 기본형과는 달리 실제 값이 저장되지 않고, 자료가 저장된 공간의 주소를 저장합니다.

  - 즉, 실제 값은 다른 곳에 있으며 값이 있는 주소를 가지고 있어서 그 주소를 참조해서 값을 가져옵니다.

- 빈 객체를 의미하는 null로 초기화시킬 수 있습니다.

- 메모리의 힙(heap)에 실제 값을 저장하고, 그 참조값(주소값)을 갖는 변수는 스택에 저장됩니다.



![참조형 변수](https://blogfiles.pstatic.net/MjAyMDA0MTdfMTQg/MDAxNTg3MDU0NjU5OTcy.iioBzIs64RamxC7UldYHfs6MbJozMoxf943HzYf_b90g.O3hL-gPMa2pl_1bmXk7l4SJvHb5jWBVM1mjMoWg76iUg.JPEG.dkfm214/3.JPG?type=w1)

## 참조형 변수의 종류
- 인터페이스 타입
- 배열 타입
- 열거 타입
- 클래스 타입

<sub>참고 문헌 : https://blog.naver.com/dkfm214/221912369571, https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B8%B0%EB%B3%B8-%EC%9E%90%EB%A3%8C%ED%98%95-%EC%A2%85%EB%A5%98-%EC%B4%9D%EC%A0%95%EB%A6%AC-int-double-char-String#%EC%8B%A4%EC%88%98_%EC%9E%90%EB%A3%8C%ED%98%95, https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EB%B3%80%EC%88%98%EC%9D%98-%EA%B8%B0%EB%B3%B8%ED%98%95-%EC%B0%B8%EC%A1%B0%ED%98%95-%ED%83%80%EC%9E%85, https://gyoogle.dev/blog/computer-language/Java/Primitive%20type%20&%20Reference%20type.html#string-class</sub>