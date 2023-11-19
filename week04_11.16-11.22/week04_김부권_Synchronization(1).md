# Synchronization

통합 프로세스는 서로 영향 받거나 주거나 한다. 공유 데이터 허가되거나 논리적 주소 공간을 공유하지만 동시성 접근은 데이터 무결성 결과를 초래한다.
그러므로 순서대로 실행되도록 보장해야함

## Race Condition
- 같은 데이터를 동시에 처리 및 접근하고 실행 결과가 access가 일어나는 특정 순서에 따라 달라지는 상황
```java
int static number = 0;
// 자바 코드를 예로 들면 static 변수로 예를 들 수 있다.
// static 변수를 사용해 context switching이 일어나면 race condition 발생
```

## Synchronization(동기화)
- race condition을 예방하기 위해 사용하는 동기화를 실행
- 시스템을 동시에 작동시키기 위해 여러 프로세스들을 조화

## Critical Section Problem(임계 영역 문제)
- 경쟁 상태가 가장 많이 발생할 수 있는 곳
- 프로세스를 최소 하나만 독점적으로 처리, 업데이트 등 할 수 있게 보장해야 함
- 두 프로세스가 동시에 실행되지 않게 해야함
- 임계 영역 Required
  1) Mutual Exclusion
     ▶ 한 프로세스를 독점적으로 실행되도록 보장
  2) Progress(: avoid deadlock)
     ▶ 교착 상태에 빠지지 않도록 선택된 섹션이 다음 프로세스에 들어가도록 보장
  3) Bounded Waiting(: avoid starvation)
     ▶ 무한대기 (기아)현상을 조절 및 제한 해줘야 함

## Peterson's Solution
- 임계 구역과 나머지 구역을 번갈아 가며 실행하는 두 개의 프로세스가 있는 경우로 한정
- 임계 영역 문제 해결을 위한 솔루션
- 개념적으론 완벽하지만 완벽히 해결할 수 있단 보장은 없음
 
  ![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/56505662-be65-4bee-bbcc-93cf6806a8ea)

## 동기화를 위한 HW 지원

### 1) Atomicity
  - 원자적 작업은 중단할 수 없는 작업 단위
  - 원자적 작업 기능 두 종류 : **test_and_set() & compare_and_swap()**

#### 1. test_and_set()
  --> 원자적으로 수행한다는 것은 인터럽트 되지 않고 수행
  --> lock이 false인 동안에 무한대기 걸어 놓고 true가 들어온다면 임계 영역 진입
  
  ![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/791446a4-0da2-4e54-b239-eef7fb18aa6d)
  
 ![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/f7fc3900-87ef-4796-85ad-f894a5403206)

#### 2. compare_and_swap()
  --> 위 명령어와 다르게 3개의 매개변수 사용
  --> lock이 0이면 1반환, 1이면 0을 반환
  
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/5e1b9b83-24aa-4cbe-ba57-9b731f25c43b)

### Atomic Variable
  - 상호 배제를 보장 (race condition을 동반한 단일 변수가 있을 수 있음)

### Memories Barriers
  - 메모리의 모든 변경사항을 다른 모든 프로세서로 전파하는 명령어를 제공하여 다른 프로세서에서 실행 중인 스레드에 메모리 변경 사항을 알림
