# Thread & Concurrency

## 스레드란?
- 프로세스 내에서 실제로 작업하는 주체 (thread id, pc, register set, stack 으로 구성)
- LWP(LightWeight Process) 라고도 불림

## 스레드 장점
1) 반응 속도
 - 프로세스 일부분이 막혀도 실행되도록 허락

2) 자원 공유
 - shared-memory 혹은 message-passing 보다 자원 공유가 쉬움

3) 경제성
 - context switching 기능보다 오버헤드가 낮고 프로세스 생성 값이 저렴

4) 확장성
 - 멀티 프로세스 생성에 유리

## 멀티 스레딩
 - 동시성에 대한 다양한 코어 사용에 효율적
 - 네개 스레드가 한 시스템에 돌아가고 있다 가정

### single-core
 - 인터리빙 법 사용
 - 인터리빙이란 데이터 사이에 끼워 넣는다란 의미

### multiple-cores
 - 병행적으로 실행

![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/abb7da39-d9e0-47c4-944d-a94ce61a7070)

## Multiple-core에 해결해야 할 문제
1) identifying tasks – 영역을 분리된 작업으로 나누기
2) balance – 각 스레드마다 균일한 업무 할당
3) data splitting – 각 데이터 또한 각 스레드에 일정히 배치
4) data dependency – 업무가 데이터 종속성을 수용하도록 동기화 보장
5) Testing & Debugging

## Amdahl’s Law
- 코어가 많을수록 속도가 빠른 것은 아니라고 주장한 법칙

![](https://velog.velcdn.com/images/dnu05043/post/b643c7f4-42fa-4969-9e47-113ffcaca572/image.png)

- S : 시스템에서 수행해야 할 부분(%)
- N : 코어의 개수

## Mulithreading Models
- User threads : 커널 위에서 작동, 프로그래밍 환경 혹은 Vm 등이 예시
- Kernel threads : Os가 직접 cpu에 접근
- ![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/f4807afd-22d0-4d7b-9dbf-07cd58725472)

## Thread libraries
- 스레드 라이브러리가 존재해야 관리 및 생성이 가능
- P(POSIX)threads, Windows thread, Java thread
