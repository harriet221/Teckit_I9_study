## ARM : Advanced RISC Machine

진보된 RISC 기기

>### RISC : Reduced Instruction Set Computer (감소된 명령 집합 컴퓨터)
### CISC : Complex Instruction Set Computer (복잡한 명령 집합 컴퓨터)

단순한 명령 집합을 가진 프로세서가 복잡한 명령 집합을 가진 프로세서(CISC)보다 훨씬 더 효율적이지 않을까?로 탄생함

>### RISC의 특징
- 단순한 명령어, 32bit (저전력)
- 하드웨어 중심 설계
- 고정 길이 명령어
- 작은 규모의 메모리 액세스, 레지스터 간의 연산에 초점
- arm 기반
### CISC의 특징 
- 복잡하고 다양한 명렁어
- 메모리 액세스에 더 많은 중요성을 두고, 명령어와 데이터를 메모리에서 직접 로드 및 저장
- 인텔 x86 기반

## arm 구조
ARM은 칩의 기본 설계 구조만 만들고, 실제 기능 추가와 최적화 부분은 개별 반도체 제조사의 영역으로 맡긴다. 따라서 물리적 설계는 같아도, 명령 집합이 모두 다르기 때문에 서로 다른 칩이 되기도 하는 것이 ARM.

>ex) ARM은 Cortex-A78이라는 CPU 코어를 설계
-> Cortex-A78은 5nm 공정으로 제조 가능 
- 삼성전자는 Cortex-A78을 5nm 공정으로 제조하여 엑시노스 2200을 출시
- TSMC는 Cortex-A78을 4nm 공정으로 제조하여 Apple A15 Bionic이라는 CPU를 출시

[안될공학 arm](https://www.youtube.com/watch?v=lyTtjx5OUW4)
[컬러스케일 - apple 실리콘](https://www.youtube.com/watch?v=W78wh-A5vW8)
