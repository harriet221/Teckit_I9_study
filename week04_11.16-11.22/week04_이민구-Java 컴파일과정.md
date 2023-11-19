Java는 OS에 독립적인 특징을 가짐.(어떤 os든 Java 프로그램은 JVM으로 기계어 해석) 
- JVM(Java Vitual Machine)이 기계어로 해석

> 컴파일(compile) - 만드는 과정(소스 코드를 바이트 코드로 변환)

> 런타임(runtime) - 실행중인 과정(바이트 코드로 변환 된 것을 실행)

## java 컴파일 순서
![image](https://camo.githubusercontent.com/af3d43865302485f944cbc6a7a7c3fcb27d3227320e5bf0b2cd8013d76507c07/687474703a2f2f7463707363686f6f6c2e636f6d2f6c656374757265732f696d675f6a6176615f70726f6772616d6d696e672e706e67)
	
    1. 개발자가 소스코드(.java) 작성
	2. 자바소스파일을 컴파일하여 java 바이트코드 (.class)(반기계어) 파일을 생성
    // 중간 단계(컴퓨터 이해 x, JVM만 이해)
	3. 각 컴파일된 바이트 코드를 클래스로더(Class Loader)에 전달
    4. 클래스로더는 동적로딩(Dynamic Loading)을 통해 필요한 클래스들을 로딩, 링크하여 JVM의 메모리(Runtime Data area)에 올림
    // 런타임 시, 바이트코드를 기계어로 바꿔주는데 이 역할을 JVM에서 함
	5. 메모리를 거쳐 실행엔진(Execution Engine)으로 간다. 실행엔진은 JVM 메모리에 올라온 바이트 코드들을 명령어 단위로 하나씩 가져와서 실행
    6. 실행과정 속에 JVM은 필요에 따라, 
       멀티 쓰레드 환경에서 여러쓰레드가 하나의 공유자원을 동시에 접속하는 것을 막는 스레드 동기화(Thread Sychromiztion)
       할당했던 메모리 중 사용이 끝난 메모리 삭제하는 가비지 컬렉션(Garbage Collecton)과 같은 관리 작업을 수행
    
 
### 바이트코드 변환 방식

	1. 인터프리터(Interpreter):
    - 바이트 코드 명령어를 하나씩 읽어서 해석하고 실행
    - 하나하나의 실행은 빠르나, 전체적인 실행 속도가 느림
    - 파이썬, 자바스크립트 등
    
	2. JIT 컴파일러(Just-In-Time Compiler) :
    - 인터프리터 방식과 컴파일 방식을 혼합한 방식, JIT 컴파일러는 실행 중에 필요한 부분을 미리 컴파일하여 기계어로 변환
    - 자바, C# 등
 
### 바이트 코드로 변환하는 이유

장점 
- 바이트 코드 변환을 통해서 CPU에 독립적이고, OS의 독립적
 
단점 
- 기계어 코드를 직접 읽는 것 보다 느림
 

## Runtime Data Area, 메모리 영역
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbpPIjI%2FbtqNCd5Hke4%2F8J0px6Bf52lK6pVrYrwvP0%2Fimg.png)

### Heap Area

GC(가비지콜렉션, Garbage Collection)의 대상이 된다.

 
[참고](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Language/%5Bjava%5D%20자바%20컴파일%20과정.md)
 
 

