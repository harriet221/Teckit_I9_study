## Garbage Collection

- java 이전 C나 C++에서는 사용자가 메모리 누수를 방지하기 위해 직접 메모리 할당과 해제를 컨트롤 
- 동적으로 할당했던 메모리 영역 중 필요 없게 된 메모리를 주기적으로 삭제하는 GC 등장

### GC의 단점
- 개발자가 메모리가 언제 해제되는지 알 수 없음
- GC 실행 중에는 다른 동작도 멈추기 때문에 오버헤드가 발생

### stop the world
- GC를 실행하기 위해 응용프로그램을 일시 중단하고, 메모리 영역을 스캔 (다른 작업 불가능)
- GC 튜닝은 이 stop the world의 시간을 줄이는 것
---
## GC의 대상
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbW5c5r%2FbtrvAb4nrdH%2FlYHuQZya8ECvEndRkQchjk%2Fimg.png)

- 객체는 ``Heap 영역``에 생성
- Method, Stack 영역은 ``객체의 주소``만 참조 
- Heap 영역에서 ``어디서든 참조하고 있지 않은 (Unreachable)`` 객체가 발생하게 되면 GC가 주기적으로 제거

## GC 동작 원리
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbGghBW%2FbtrvvDgIHRO%2FHxoX3w9skgah3xFVhfEgD0%2Fimg.png)

### Mark and Sweep 알고리즘
#### 메모리 해제 기준 
- 루트에서부터 해당 객체에 접근 가능한지 여부
#### Mark 과정
- 루트로부터 그래프 순회를 통해 연결된 객체를 찾아내 마킹
#### Sweep 과정
- unreachable 객체를 Heap에서 제거 
#### Compact 과정 
- sweep 후 분산된 객체들을 Heap의 시작 주소로 모아 메모리가 할당된 부분과 그렇지 않은 부분으로 압축 (GC 종류에 따라 하지 않는 경우도 있음)


### 힙의 구조 
![힙 구조](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbti1oP%2FbtrvtcdoBC9%2FupBBOdB4mJF6tfyhL8GPbK%2Fimg.png)

Young generation에서 발생하는 GC -> ``minor GC`` 

Old generation에서 발생하는 GC -> ``major GC``

>## GC 동작 과정 
### 1단계
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F7pVmj%2Fbtrvu28jcRt%2FIy5eB9flQ8L4eIkc0a1FX1%2Fimg.png)
- 객체가 처음 생성 되고 Eden 영역에 age-bit 0으로 할당
- Minor GC에서 살아 남을 때마다 1씩 증가
### 2단계
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcTWRqo%2FbtrvxlfT2KU%2FgIDFZpUapbTZTKR1Gi16M0%2Fimg.png)
- Eden 영역에 객체가 쌓이면 Minor GC가 일어나고 참조 정도에 따라 Servivar 0으로 이동
### 3단계
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb42htO%2FbtrvuPvhcQ2%2FHwXDNmku8NbhSkaGoJEywK%2Fimg.png)
- 계속해서 Eden 영역은 신규 객체 생성, 비어있는 Survival 1로 이동하고 살아남은 객체들은 age 1씩 증가1
### 4단계
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdpYphN%2FbtrvocRXzk2%2FPANFhltyaGtzuDak9nqd61%2Fimg.png)
- minor GC가 일어나면 비어있는 Survival 0으로 이동 시킨뒤 age 1 증가, 
- 이 과정 계속 반복
### 5단계
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FGvbFe%2FbtrvqaMQzF5%2F2pYF0QKjwBZWF7EtYNJ8OK%2Fimg.png)
- JVM에서 설정해놓은 age bit에 도달하게 되면 Old generation 영역으로 이동 
 -> 이 과정을 프로모션(= Promotion) 이라고 함
### 6단계
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb015X4%2FbtrvtcRX3Go%2FDG6GyfMsZv0xgJRujfOeRK%2Fimg.png)
- Old영역에 할당된 메모리 허용치를 넘게 되면, Old 영역에 있는 모든 객체들을 검사하여 참조되지 않는 객체들을 한꺼번에 삭제하는 GC가 실행
- Old generation 영역의 메모리를 회수하는 GC를 ``Major GC``
- Major GC는 시간이 오래 걸리고, 이때 GC를 실행하는 스레드를 제외한 모든 스레드는 작업을 멈추게 됨 (=``Stop-the-World``)

[참고 및 출처](https://coding-factory.tistory.com/829)
