# PCB & Context Switching

## 1. 정의

#### PCB(Process Control Block)

운영 체제에서 프로세스를 관리하기 위한 자료구조. 각 프로세스에 대한 정보, 즉 **프로세스 메타데이터**를 저장하고, 이를 통해 프로세스의 상태 및 동작을 추적하는 데 사용됨. 한 PCB 안에는 한 프로세스의 정보가 담김.

> 프로그램 실행 → 프로세스 생성 → 프로세스 주소 공간 할당 (코드, 데이터, 스택) → 해당 프로세스의 메타데이터들이 PCB에 저장

<br>

## 2. 프로세스 메타데이터

#### Process Management

: 프로세스가 여러개일 때, CPU가 다양한 [스케줄링 기법](https://github.com/harriet221/Teckit_I9_study/blob/main/week03_11.09-11.15/week03_%EC%9C%A4%EC%84%9C%EC%A0%95-CPU%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81.md)을 통해 각 프로세스의 작업을 관리하는 것

CPU에서는 프로세스의 상태에 따라 교체작업이 이루어짐. (interrupt가 발생해서 할당받은 프로세스가 waiting(대기) 상태가 되고 다른 프로세스를 running(실행)으로 바꿔 올릴 때 등)
이때, **앞으로 다시 수행할 대기 중인 프로세스에 관한 정보** 필요.

각 프로세스의 정보 = **Process Metadata**

- **Process ID**: 각 프로세스에 할당된 고유한 식별자
- **Process State**: 프로세스의 현재 상태
- **Process Priority**: 프로세스 스케줄링에서 사용되는 우선순위 정보
- **CPU Registers**: CPU 레지스터의 현재 값 (재실행 시 레지스터 복원용)
- **Program Counter**: 프로세스가 다음에 실행할 명령어의 주소를 가리키는 레지스터 값
- **Owner / Parent Process ID**: 현재 프로세스를 생성한 상위 프로세스의 식별자
- **Accounting Information**: CPU 사용량(CPU Usage), 실행 시간, 메모리 사용량(Memeory Usage) 등과 같은 계정 정보
- **Resource Usage Information**: 할당된 자원, 파일 사용 정보

그 외에, 프로세스의 가상 메모리 주소 공간이나, I/O 상태 및 정보 등을 포함함.

<br>

## 3. 관리

: PCB는 운영 체제 커널 내에서 관리되며, 각 프로세스에 대한 정보를 저장하여 프로세스 스케줄링 및 관리 작업에 사용함.

주로 PCB List Head에 PCB가 생성될 때마다 우선순위에 따라 저장되고 헤드 포인터가 붙는 Linked List 방식으로 관리함. 프로세스가 생성되면 해당 PCB가 생성되고 프로세스 완료시 제거됨. 주소값으로 연결이 이루어져 있는 연결리스트이기 때문에 삽입 / 삭제가 용이하기 때문.

이렇게 수행 중인 프로세스를 변경할 때, CPU의 레지스터 정보가 변경되는 것을 **Context Switching**이라고 함.

<br>

## 4. Context Switching

: CPU가 이전의 프로세스 상태를 PCB에 보관하고, 또 다른 프로세스의 정보를 PCB에서 읽어 레지스터에 적재하는 과정

보통, 인터럽트 발생 / 실행 중인 CPU 사용 허가시간 모두 소모 / 입출력을 위해 대기해야 하는 경우에 진행됨.

즉, Ready → Running, Running → Ready, Running → Waiting 등 **프로세스 상태 변경 시** 진행하는 과정.

### Context Switching의 Overhead 감수

프로세스 작업 중에는 overhead(과부하)를 감수해야 하는 상황이 있음.

ex/ 프로세스를 수행하다가 입출력 이벤트가 발생해서 해당 프로세스를 대기 상태로 전환시킨 경우.<br>
→ 이때, CPU를 그냥 놀게 놔두는 것보다 다른 프로세스 작업을 수행하게 하는 것이 효율적.

즉, CPU의 효율적인 사용을 위해 = CPU가 놀지 않도록 하고, 사용자에게 빠르게 작업 결과를 제공해주기 위해 어느정도의 오버헤드는 감수하는 것. 기준을 넘지 않기 위해서 CPU 스케줄링으로 관리.
