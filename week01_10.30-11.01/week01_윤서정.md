# Introduction & O/S Structures

## What is OS?

**컴퓨터**(불확실한 상황에 대한 수치적 표현(최소 단위: bit)인 정보를 처리하는 범용적인 하드웨어) **시스템 운영 소프트웨어**

#### 폰 노이만 구조

- 메모리에 프로그램을 내장하는 구조
- ISA 명령어 집합의 fetch & execute 사이클을 통한 운영

RAM -> CPU : fetch<br>
program -> process in CPU : execute<br>

### OS가 하는 일

- 하드웨어와 어플리케이션(그 너머의 사용자) 사이에서 시스템 서비스 제공
- 주로 제공하는 서비스:

  - 유저 인터페이스(User Interface)
  - 프로그램의 실행(Program execution)
  - 입출력 연산(I/O operation)
  - 파일 시스템 조작(File-system manipulation)
  - 에러 탐색(Error detection)
  - 자원 할당(Resource allocation)
  - 로깅(Logging) : 애플리케이션의 동작&상태 (log) 기록
  - 보호 및 보안(Protection and security)

어플리케이션은 System Calls을 통해 OS와 통신한다.
이때 하드웨어와 소프트웨어 간의 중재자 역할을 하는 커널이 OS의 핵심 부분.<br>
결론적으로, 운영 체제 = 컴퓨터 시스템의 모든 측면을 관리하는 소프트웨어.<br>

### 예상 QnA

Q: 운영 체제의 주요 역할과 운영 체제가 필요한 이유는?<br>
A: <br>
자원 관리: 운영 체제는 시스템의 하드웨어 자원(프로세서, 메모리, 저장 장치, 입출력 장치 등)을 효율적으로 할당하고 관리한다.<br>
프로세스 관리: 프로세스를 생성, 스케줄링 및 제어하여 다중 작업 환경을 제공한다.<br>
메모리 관리: 물리적 메모리와 가상 메모리를 관리하여 프로그램의 실행을 지원하고 메모리 관리 오버헤드를 최소화한다.<br>
파일 시스템 관리: 파일 및 디렉터리를 생성, 읽기, 쓰기 및 삭제할 수 있는 파일 시스템을 제공한다.<br>
사용자 인터페이스: 사용자와 하드웨어 간의 상호 작용을 담당하는 CLI(Command Line Interface) 또는 GUI(Graphical User Interface)를 제공한다.<br>
보안 및 권한 관리: 데이터 보안을 유지하고 사용자 권한을 관리하여 무단 액세스를 방지한다.<br>
<br>
=> 컴퓨터는 한번에 한가지 일만 처리하지 않는다. 이러한 컴퓨터의 multitasking(= multiprocessing = concurrency)에서 가장 중요한 것은 여러 어플리케이션이 동시에 실행되면서도 서로 간섭하지 않고 한정된 자원을 효율적으로 사용하는 것이다. 이에 다중 작업에서의 CPU 스케쥴링과 공유 자원 관리, 인터럽트 등에서 발생하는 지연과 에러 처리, 그리고 시스템 전체의 보안을 관리하는 운영체제의 존재는 필수적이다.
