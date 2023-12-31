# 로드 밸런싱(Load Balancing)

## 1. 정의와 목적

: 여러 대의 서버나 네트워크 장치에 가해지는 부하를 균형 있게 분산시켜서 효율적으로 자원을 활용하고 서비스의 안정성을 높이는 기술<br>

-> 서버 자원을 균형 있게 분산하여 전체 시스템의 성능을 향상시키고 안정성을 높이는 것이 목적. 주로 대규모 웹 서비스, 데이터베이스 서버, 애플리케이션 서버 등에서 사용되며, 트래픽이나 부하를 효율적으로 분산하여 각 서버에 일관된 성능을 제공함.

## 2. 사용 이유

웹사이트에 접속하는 모든 사용자에 대해 모든 트래픽을 감당하기엔 1대의 서버로는 부족함. 대안은 다음과 같음.

- 하드웨어의 성능을 올리는 Scale-up
- 여러대의 서버가 나눠서 일하도록 만드는 Scale-out

하드웨어 향상 비용이 고가인 점, 서버가 여러대면 무중단 서비스를 제공하는 환경 구성이 용이한 점 등을 고려해 Scale-out 방식이 효과적. 이때, 여러 서버에게 균등하게 트래픽을 분산시켜주는 것 = 로드 밸런싱

결국 로드 밸런싱 = 분산식 웹 서비스<br>
→ 여러 서버에 부하(Load)를 나누어주는 역할

Load Balancer를 클라이언트와 서버 사이에 두고, 부하가 일어나지 않도록 클라이언트의 요청에 따른 작업을 여러 서버에 분산하여 수행하게 하는 방식.

## 3. 사용 방식

이러한 로드 밸런서는 하드웨어 기반이 될 수도 있고, 소프트웨어 기반이 될 수도 있음. 상용 제품부터 오픈 소스 솔루션까지 다양한 형태로 제공.

#### 로드 밸런서가 서버를 선택하는 방식

- 라운드 로빈(Round Robin) : [CPU 스케줄링](https://github.com/harriet221/Teckit_I9_study/blob/main/week03_11.09-11.15/week03_%EC%9C%A4%EC%84%9C%EC%A0%95-CPU%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81.md)의 라운드 로빈 방식 활용 (각 서버에 요청을 순서대로 배분)
- 가중치 기반(Weighted Round Robin): 서버에 가중치를 부여하여 각 서버가 다룰 수 있는 부하의 정도에 따라 각자 다른 작업량 분배
- 자원 기반(Resource-based Load Balancing): 각 서버의 현재 자원 사용량을 고려하여 자원 사용량이 낮은 서버에 우선적으로 트래픽 부여
- 최소 응답 시간 기반(Least Response Time): 각 서버의 응답 시간을 측정하여 가장 빠른 응답을 보내는 서버에 트래픽 부여
- 최소 연결 수 기반(Least Connections) : 연결 개수가 가장 적은 서버 선택 (트래픽으로 인해 세션이 길어지는 경우 권장됨)
- Source (IP Hash) : 클라이언트의 IP를 해싱하여 분배 (특정 사용자가 항상 같은 서버로 라우팅되도록 보장)
- Random : 요청을 무작위로 선택하여 서버에 전달

로드 밸런서는 이러한 알고리즘을 조합하여 사용할 수 있으며, 선택한 알고리즘은 서버 구성, 트래픽 패턴, 성능 요구 등에 따라 결정됨.

또한, 로드 밸런서의 장애에 대비하여 로드 밸런서를 **이중화**하여 대비함.

#### Active 상태와 Passive 상태

: 두 개의 로드 밸런서를 동시에 운영하고, 하나의 로드 밸런서가 장애 발생 시 다른 로드 밸런서가 이를 대체하여 서비스를 계속할 수 있도록 함 = 서버 환경의 안정성과 가용성 향상을 위한 방법
