# 운영체제
- 컴퓨터 하드웨어를 관리하는 소프트웨어
- 컴퓨터에서 항상 실행 중인 프로그램으로, kernel이라고 부른다.
- 어플리케이션 프로그램을 작성하는 사람이 하드웨어를 직접 건드리기는 어려우므로 OS에게 대신 요청을 해서 처리한다.
- OS는 프로세스, 자원, 유저 인터페이스 등을 관리한다.

# Interrupts
![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/ca37d85a-673f-461c-adf4-8d712d6979dd)

- Interrupt는 CPU와 하드웨어가 통신하는 방식으로, 하드웨어에서 interrupt를 발생시키면 CPU에 signal이 전송된다.
- 예를 들어, I/O 디바이스에서 A키를 눌렀을 때, 키보드에 있는 컨트롤러가 그것을 CPU에게 알려주고, 그럼 CPU는 그것을 받아서 처리한다.

# 폰 노이만 아키텍처
![https://www.computerhope.com/jargon/m/machcycl.htm](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/16eb2b40-4146-4bb0-876b-b5b75db98a32)

- Instruction-execution cycle
- Instruction은 컴퓨터에 내릴 수 있는 명령어
- 명령어들로 구성된 프로그램을 메모리에 올려서 메모리에 있는 그 명령어를 CPU가 하나씩 fetch하고 execute함

# Symmetric Multiprocessing
![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/772ff79c-10da-4b2b-9880-7c12809aae92)

- 가장 일반적인 multiprocessor 시스템
- 메모리는 하나만 존재하고, 이 메모리에 여러 CPU가 연결되어 있는 구조
- 각 CPU에는 자체 register와 cache가 존재하지만, 모든 프로세서는 system bus를 통해 메모리를 공유한다.

## Multicore
![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/a52682ff-2d2f-4d3e-9431-ba714e376919)

- 하나의 프로세서 안에서 통신하는 게 더 빠름
- 하나의 프로세서 안에 CPU core를 여러 개 두는 방식
- 각 CPU에는 자체 register와 cache가 존재하고, 공유 cache도 존재함

# Multiprogramming
![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/9c2c57fc-7d81-4613-af58-4a4b3b2ccc2f)

- 여러 개의 프로그램을 동시에 메모리에 올려두는 것
- 한번에 한 개 이상의 프로그램이 동작함
- CPU 사용 효율을 높일 수 있음

## Multitasking
- Multiprogramming의 논리적 확장
- CPU가 여러 프로세스를 자주 전환하여 실행되며, 사용자에게 빠른 응답 시간 제공
- 하나의 CPU를 가지고 시간을 나눠서(time-sharing, 시분할) 수행함

# Operation modes
![image](https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/f96e19d9-386b-4b0e-8260-5ebe6fce35a2)

- 유저 모드와 커널 모드 존재
- 프로세스가 유저 모드에서 실행되다가 system call이 발생하면 커널 모드로 들어감
- 커널에서 받은 요청을 수행한 뒤 다시 유저 모드로 돌아감
- 커널 모드에서는 직접적으로 하드웨어 제어가 가능하지만, 유저 모드에서는 불가능하므로 보호할 수 있음
