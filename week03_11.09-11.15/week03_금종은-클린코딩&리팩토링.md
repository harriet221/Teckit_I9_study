# [CS] 클린코딩 & 리팩토링

# 클린코드

코드를 작성하는 의도와 목적이 명확하며, 다른 사람이 쉽게 읽을 수 있어야 한다.

가독성이 높은 코드를 의미한다.

## 조건

- 네이밍을 잘 해야 한다.
- 오류가 없어야 한다.
- 중복이 없어야 한다.
- 의존성을 줄여야 한다.
- 클래스 혹은 메소드가 한 가지 일만 처리해야 한다.

## 규칙

### 1. Naming(명명)

변수, 클래스, 메소드에 그 의도가 분명한 이름을 사용한다.

```java
int daySinceCreation;
String filePath;

public void setName() {}
```

잘못된 정보를 전달할 수 있는 이름은 사용하지 않는다.

범용적으로 사용되는 단어는 사용하지 않는다.

연속된 숫자나 불용어를 덧붙이는 방식은 피해야 한다.

### 2. Comment(주석)

코드를 읽는 사람이 코드를 작성한 사람만큼 잘 이해할 수 있도록 도와야 한다.

주석은 반드시 달아야 할 이유가 있는 경우에만 작성하도록 한다.

코드를 빠르게 유추할 수 있는 내용에는 주석을 사용하지 않는 것이 좋다.

주석으로 코드를 설명하지 않고, 최대한 코드로 이해할 수 있게 코드를 잘 작성하는 게 더 중요하다

[[클린 코드] 4장 - 주석 (Comments)](https://effortguy.tistory.com/187)

### 3. Aesthetics(꾸미기)

규칙적인 들여쓰기와 줄바꿈으로 가독성을 향상시킨다.

일관성있고 간결한 패턴을 적용하여 줄바꿈을 한다.

### 4. Making control flow easy to read(흐름제어 만들기)

1. 비교할 때는 왼쪽에 변수, 오른쪽에 상수
    
    `if (length >= 10) {...}`
    
2. 부정이 아닌, 긍정을 다루기
    
    ```java
    if (a == b) {
    } else {
    }
    
    public boolean isFull() {}
    if (isFull()) {}
    ```
    
3. `if-else`문을 사용하며, 삼항연산자는 매우 간단한 경우에만 사용한다.
4. `do-while`은 가급적 피한다.</br>
[Do Statement (do-while)에 관한 소고](http://rapapa.net/?p=3277)

### 5. Function(함수)

함수는 가급적 작게, 한번에 하나의 기능만 수행하도록 작성한다.

```java
public void addPharse() {
		System.out.print("명령) ");
		String cmd = sc.nextLine();
		Request rq = new Request(cmd);

		if (cmd.equals("등록")) {
			Phrase ph = new Phrase();
			System.out.print("명언: ");
			String content = sc.nextLine();
			System.out.print("작가: ");
			String author = sc.nextLine();
			list.add(new Phrase(content, author));
			System.out.println("명령이 등록되었습니다.");
		}
}
```

여기서 명언을 등록하는 함수를 작성하고자 했는데, 명령을 입력하는 기능까지 포함하고 있다.

명령을 입력하는 기능은 별도의 함수로 작성해서, `"등록"`을 입력받았을 때 `addPhrase()`에서는 `if`문 내부의 기능만 수행하도록 작성하는 게 좋다.

# 리팩토링

프로그램의 외부 동작은 그대로 둔 채, 내부의 코드만을 정리하며 개선시키는 것이다.

레거시 코드(테스트가 불가능하거나 이해하기 어려운 코드)를 클린 코드로 만드는 것이다.

이 작업은 코드의 가독성을 높이고, 향후에 이루어질 유지보수에 큰 도움이 된다.

리팩토링의 목적은 소프트웨어를 더 이해하기 쉽고 수정하기도 쉽게 만들어주는 것으로, 개발 속도를 증가시킬 수 있다.

## 리팩토링이 필요한 코드

- 중복 코드
- 긴 메소드
- 거대한 클래스
- Switch 문

[[Clean Code] 함수 (Function) : Switch 문](https://goodgid.github.io/Clean-Code-Function-Switch/#google_vignette)

## 리팩토링 예제

[gyoogle / tech-interview-for-developer / Computer Science / Software Engineering / Clean Code & Refactoring.md - 리팩토링 예제](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Software%20Engineering/Clean%20Code%20%26%20Refactoring.md#%EB%A6%AC%ED%8C%A9%ED%86%A0%EB%A7%81-%EC%98%88%EC%A0%9C)

# 클린코드와 리팩토링의 차이

리팩토링이 더 넓은 의미를 가진다.

클린코드는 단순히 가독성을 높이기 위한 작업으로 이루어져 있다.

리팩토링은 클린코드를 포함하여 유지보수를 위한 코드 개선이 이루어진다.

클린코드는 설계부터 잘 이루어져 있는 것이 중요하고, 리팩토링은 결과물이 나온 이후에 수정이나 추가 작업을 진행하며 개선해나가는 것이 올바른 방향이다.

---

> [참고 사이트]</br>
[yuseogi0218.log - 클린코드 / 리팩토링 / 시큐어 코딩](https://velog.io/@yuseogi0218/%ED%81%B4%EB%A6%B0%EC%BD%94%EB%93%9C-%EB%A6%AC%ED%8C%A9%ED%86%A0%EB%A7%81-%EC%8B%9C%ED%81%90%EC%96%B4-%EC%BD%94%EB%94%A9)
</br>[gyoogle / tech-interview-for-developer / Computer Science / Software Engineering / Clean Code & Refactoring.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Software%20Engineering/Clean%20Code%20%26%20Refactoring.md)
