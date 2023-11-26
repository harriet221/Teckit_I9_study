# CPU Scheduling

## 스케쥴링
- 운영체제에서 기본적인 기능
- 동시에 프로세스 운영
- CPU 이용률을 극대화
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/59aa0865-cbf6-4dfb-a662-a28251fd1c6a)

## CPU 스케줄러
- 실행 할 준비가 된 메모리의 프로세스 중에서 프로세스 선택하고 해당 프로세스에 할당하는 기법
- 선점형과 비 선점형으로 나뉨

## Preemptive
- 먼저 입장한 프로세스 자리를 뺏을 수 있음
- 대표적인 선점 : SRTN, RR, Priority etc

## Non_Preemptive
- 먼저 입장한 프로세스의 자리를 뺏을 수 없음
- 대표적인 비선점 : FCFS,SJF etc

## Dispatcher
- CPU Scheduler에 의해 선택된 프로세스에 CPU 코어 제어 권한을 부여하는 기능
- Context Swithing 기능과 유사
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/31f699bd-727f-4dee-b437-5b98c28e5196)

## Scheduling Criteria
1. CPU 이용률 : 가능한 많이 CPU 사용
2. 처리량 : 단위 시간 내 프로세스 완성
3. 처리 시간 : 실행시간부터 종료까지 시간 최소화
4. 대기 시간 : 레디 큐에서 대기 시간을 최소화 해야함
5. 응답 시간 : 응답 시간 최대한 빠르게

## FCFS
- 선입선출 형태 (가장 간단한 알고리즘)
- 프로세스 크기와 중요도를 고려하지 않고 순차적으로 처리
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/d3a50ca8-63de-4074-bddc-d11cb792e8f6)

## SJF
- Shortest Job First의 약자로 작업량이 쩗은 순으로 실행
- 최소 대기시간을 보장
- 하지만 CPU Burst 시간을 알 수 없기에 가장 짧은 처리량이 무엇인지 알 수 없음
- 대략적으로 처리 시간을 구해 예상
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/a04daef4-8fb4-4366-99d0-6a0d4401578f)

## SRTF
- 선점형 SJF가 SRTF라고 할 수 있음
- 실행하고 있는 프로세스 보다 새로 들어온 프로세스가 더 짧은 경우 선점 가능
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/03ede07a-6b07-48e6-86da-c2d6d5bbe6d3)

## RR
- 시분할이 존재하는 선점형 FCFS
- 레디 큐를 원형 큐처럼
- 시분할 > CPU Burst
 👉 프로새스 자체가 CPU를 자발적으로 해제, 스케줄러는 준비 대기열의 다음 프로세스로 진행
- 시분할 < CPU Burst
 👉 시분할 시점에 interrupt 발생
 👉 context switching 발생하며 ready queue에 다시 적재

## Prioirity-base Scheduling
- 가장 중요도가 높은 프로세스를 할당, 만일 중요도가 같다면 FCFS처리
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/e16d94da-825a-429d-948f-a5ab37910d6e)
- Priority Scheduling은 선점 및 비선점 가능
- 기아 현상 문제가 발생할 수도 있음 --> Aging 기법 이용

## MQL
- 우선순위마다 준비 큐가 존재하며 각 큐마다 RR과 FCFS 이용
- 프로세스 성격에 따라 우선순위가 다름
- 큐들 간 프로세스 이동이 불가능하기에 유연성이 떨어짐
- 우선순위가 낮은 큐는 대기시간이 많이 걸릴 수도 있어 기아 현상 발생할 수 있음

## MLFQ
- 다단계 큐 + 동적으로 프로세스 우선순위 변화 가능
- 단계가 내려갈 수록 시간 할당량이 증가
- 큐 사이 프로세스 이동 가능
- 맨 아래 큐에서 너무 오래 대기 시, 상위 큐로 이동 가능 (Aging 기법)
