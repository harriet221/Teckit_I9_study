운영체제란?<br>
•  컴퓨터 시스템을 운용하는 시스템

컴퓨터란?<br>
•  정보를 처리하는 기계

정보란?<br>
•  불확실성을 측정하는 정량적 표현<br>
o  정보의 최소 단위 : bit(binary digit)

컴퓨터의 정보 처리 방법<br>
•  정보의 처리 : 정보의 상태 변환(0에서 1로, 1에서 0으로)<br>
•  전류의 양을 조절하거나, 끄거나 킴을 신호로서 정보의 전달과 연산이 가능하다.<br>
o  부울 대수(Boolean Algebra) : NOT, AND, OR<br>
o  논리 게이트 : NOT, AND, OR, XOR, NAND, NOR<br>
o  논리 회로 : IC, LSI, VLSI, ULSI, SoC, ... (라지 스케일, 베리라지스케일, 울트라라지스케일)<br>

컴퓨터의 정보처리의 의미  
•  덧셈 : 반가산기, 전가산기<br>
•  뺄셈 : 2의 보수 표현법<br>
•  곱셈과 나숫셈 : 덧셈과 뺄셈의 반복<br>
•  실수 연산 : 부동 소수점 표현법<br>
•  함수 : GOTO<br>

컴퓨터는 범용성(universality)이 있다<br>
•  NOT, AND, OR 게이트(=NAND 게이트)<br>
o  NAND 게이트만으로 모든 계산을 할 수 있는 것이 수학적으로 증명이 되있다.<br>
•  범용 컴퓨터 : general-purpose computer<br>

그 목적을 제외한 다른 목적으로 사용할 수 없는 경우는 컴퓨터가 아닌 칼큘레이터라 부른다.<br>
하지만 컴퓨터가 모든 것을 계산할 순 없다.<br>
•  계산가능성 : computability<br>
•  Turing-computable : 튜링 머신으로 계산가능한 것<br>
•  정지 문제 : Halting Problem : 튜링 머신으로 풀 수 없는 문제<br>
컴퓨터의 할아버지<br>

Alan Turing - Turing Machine 의 개발자<br>
컴퓨터의 아버지<br>

John von Neumann - ISA: Instruction Set Architecture<br>
앨런 튜링<br>
•  현대의 운영체제의 기반이 되는 튜링머신을 개발<br>
o  Universal Turing Machine - Operating System(운영체제)<br>
o  Head - CPU<br>
o  Tape - RAM<br>
o  Turing Machines - Application Programs<br>

폰 노이만<br>
•  처음으로 stored(내장형) 프로그램 방식을 도입<br>
o  내장형 프로그램 : 프로그램을 저장하는 컴퓨터<br>
o  본래 프로그램은 하드웨어의 영역이었지만 이를 통해 소프트웨어 교체만으로 프로그램을 사용 가능<br>
o  이 구조를 폰 노이만 아키텍처 (ISA) 라고 부른다<br>

프로그램이란?<br>
•  명령어들의 집합<br>
o  컴퓨터 하드웨어에게 특정 업무를 실행시키는 명령어들의 집합<br>

운영체제도 프로그램이다<br>
•  시스템 서비스를 응용 프로그램에게 제공<br>
o  컴퓨터에서 항상 동작하는 프로그램<br>
o  애플리케이션 제공자들은 운영체제 덕분에 하드웨어에 접근하지 않아도 됀다.<br>
o  프로세스, 리소스, 사용자 환경을 운영체제가 모두 관리<br>

컴퓨터란?<br>
기능을 업데이트하거나 추가할 수 있는 범용성을 가진 모든 기기들<br>

운영체제란 컴퓨터 하드웨어를 관리하는 소프트웨어<br>

운영체제의 역할<br>
•  응용 프로그래밍의 기반 제공<br>
•  컴퓨터 유저와 컴퓨터 하드웨어 간의 중간 매개 역할<br>

컴퓨터 시스탬의 요소<br>
•  하드웨어 (hardware)<br>
•  운영체제 (operating system)<br>
•  응용 프로그램 (application programs)<br>
•  사용자 (user)<br>

운영체제에 대한 보편적으로 정해진 정의는 존재하지 않는다<br>
가장 흔한 정의는 "언제나 구동되고 있는 하나의 프로그램"으로<br>
보통 커널(kernel)이라고 불린다.<br>
커널에서 시스템 프로그램과 응용 프로그램에 대한 인터페이스를 제공한다.<br>
컴퓨터의 구조<br>

클래식한 컴퓨터의 구조<br>
•  하나 이상의 CPU 보유<br>
•  버스(bus)를 통해 연결된 여러개의 디바이스 컨트롤러<br>

bootstrap program 이란?<br>
컴퓨터가 시작될 시 가장 먼저 실행되는 프로그램<br>
•  운영체제를 로딩하는 일을 해줘야한다.<br>
•  하드디스크에 있는 운영체제(커널)를 메모리에 로딩해주는 역할<br>

인터럽트(Interrupts)란?<br>
•  cpu와 프로세스하고 I/O 디바이스 가 서로 통신하는 방법 중 하나<br>
•  하드웨어는 언제든 시스템 버스를 통해 cpu에게 신호를 주는 방식으로 인터럽트를 작동시킬 수 있다<br>

폰 노이만 아키택처의 명령 실행 주기<br>
1. 메모리를 명령어에서 가져온 후 명령어 레지스터에 저장<br>
2. 해독(피연산자가 필요하다면 메모리에서 가져와 내부 레지스터에 저장된다)<br>
3. 피연산자에 명령어가 실행된 후 메모리에 다시 저장<br>

저장시스템은 용량이나 속도에 따라 여러개의 계층으로 구성되어 있다.<br>

I/O Structure<br>
•  OS(운영체제)의 상당 부분은 (I/O) 입출력에 할애된다<br>

컴퓨터 구성 요소의 정의<br>
•  CPU - 명령들을 실행하는 하드웨어<br>
•  Processor - 한개 이상의 CPU가 내장된 칩<br>
•  Core - 프로세서의 계산 및 명령 처리 작업을 담당<br>
•  Multicore - 여러개의 CPU가 들어있는 하나의 코어<br>
•  Multiprocessor - Multicore와 의미가 같다<br>

Symmetric multiprocessing (SMP)<br>
•  가장 일반적인 멀티프로세서 시스탬<br>
•  각각의 CPU 가 레지스터와 캐쉬를 가지고 합쳐져있다.<br>
•  각각 다른 태스크를 수행한다<br>

Multi-core design<br>
•  한 프로세서 하나에 여러개의 코어가 붙어있는 것을 멀티코어 라 한다.<br>
o  멀티코어들이 여러개 붙어있는 것을 멀티프로세서 라고 한다.<br>

Multiprogramming<br>
•  동시간에 한개 이상의 프로그램이 실행되는 방식<br>
•  여러개의 프로세스를 동시에 메모리에 올리는 방식<br>
o  CPU 사용효율을 높일 수 있다<br>
•  이를 통해 Multitaking(=multiprocessing) 을 할 수 있다.<br>

Multitasking (= multiprocessing)<br>
•  멀티프로그래밍의 논리적 확장<br>
•  CPU가 작업을 수시로 전환하여 사용자가 동시에 여러 작업을 할 수 있게끔 한다<br>

CPU scheduling<br>
•  여러개의 프로세스가 동시에 준비가 되었을 때 시스템에서 다음 프로세스를 고르는 것<br>
•  목표는 최고의 cpu 효율<br>

운영체제 모드<br>
•  유저모드와 커널모드로 나뉜다<br>
•  부정한 프로그램이 다른 프로그램의 구동을 방해하는 상황을 막는다<br>

Virtualization (가상화)<br>
•  하나의 컴퓨터에서 여러개의 구동환경(운영체제)을 사용할 수 있는 기술<br>
•  VMM (Virtual Machine Manager)<br>
o  가상화된 환경을 관리하고 동작시키는 소프트웨어<br>
o  VMware, XEN, WSL, and so on.<br>

다양한 컴퓨터 환경에서의 운영체제<br>
•  Traditional Computing<br>
o  현대의 전형적인 컴퓨터<br>
•  Moblie Computing<br>
o  안드로이드, 아이폰<br>
•  Client-Server Computing<br>
o  Web<br>
•  Peer-to-Peer Computing<br>
o  토렌트, 비트코인, 블록체인<br>
•  Cloud Computing<br>
o  유저는 터미널을 통해 클라우드가 제공하는 서비스를 활용하는 환경<br>
o  AWS, Azure, GCP, 네이버 클라우드<br>
•  Real-Time Embedded Systems<br>
o  하드웨어를 실시간으로 조종하는 시스템<br>
o  자동차 엔진, 공장용 로봇<br>

운영체제는 프로그램이 실행될 수 있는 다음과 같은 환경을 제공한다<br>
•  유저 인터페이스 (user interfaces)<br>
•  프로그램 실행 (program excution)<br>
•  입출력 작업 (I/O operation)<br>
•  파일 시스템 처리 (file systems)<br>
•  통신 (communication)<br>
•  오차 검출 (error detection)<br>
•  리소스 할당 (resource allocation)<br>
•  Logging<br>
•  데이터 보호, 보안 (protection and security)<br>

사용자가 운영체제에 접속하는 세가지 방법<br>
•  CLI : command line interface, or command interpreter<br>
o  명령어 기반 인터페이스<br>
o  shell<br>
•  GUI : graphical user interface<br>
o  그래픽 환경 기반의 마우스 입력 사용자 인터페이스<br>
o  Windows, Aqua for MacOS, etc<br>
•  Touch-Screen Interface<br>
o  그래픽 환경 기반의 터치 입력 사용자 인터페이스<br>
o  Android UI, iphone UI, etc<br>

System calls<br>
•  운영체제가 제공해주는 서비스들을 호출하는 방법<br>
•  API : Application Programming Interface<br>
