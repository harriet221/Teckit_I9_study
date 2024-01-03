# DHCP (Dynamic Host Configuration Protocol)

## 1. 정의

호스트(서버)의 해당 IP 주소와 TCP/IP 프로토콜의 기타 정보를 IP 호스트(클라이언트)에 자동으로 제공하는 프로토콜. 네트워크에 사용되는 IP주소를 DHCP서버가 중앙집중식으로 관리하기 때문에 클라이언트-서버 모델에 기반함. 호스트는 이를 통해 DHCP 서버에서 필요한 TCP/IP 구성 정보를 가져올 수 있음.

## 2. DHCP 서버

DHCP 서버의 주요 역할은 클라이언트에 IP 주소를 제공하는 것으로, 주로 작은 규모의 로컬 네트워크, 가정 네트워크, 기업 내부 네트워크 등에서 사용됨. 각 DHCP 서버는 DHCP를 사용하여 해당 네트워크에 연결된 디바이스들에게 자동으로 IP 주소, 서브넷 마스크, 기본 게이트웨이, DNS 서버 등의 네트워크 설정 정보를 할당함.

### DHCP 서버의 역할

- 동적 IP 주소 할당: 네트워크에 연결된 디바이스들에게 동적으로 IP 주소를 할당함. 이로써 중복된 IP 주소 할당을 방지하고 네트워크 관리를 간편하게 해줌.

- 네트워크 설정 제공: 클라이언트 디바이스에게 서브넷 마스크, 기본 게이트웨이, DNS 서버 등의 네트워크 설정 정보 제공.

- 임대 시간 설정: 할당된 IP 주소의 사용을 일정 기간 동안 제한함. (= 임대 시간(Lease Time), 클라이언트는 이 기간이 만료되면 DHCP 서버에게 새로운 IP 주소를 요청해야 함)

DHCP의 경우 Application 계층 프로토콜로 분류하며, wifi의 경우 공유기가 DHCP 서버 역할을 수행함.

## 3. IP 할당 트랜잭션

DHCP 서버와 클라이언트 간 브로드캐스트 통해 `discover → offer → request → Ack` 4단계를 거쳐 IP 할당.

### DORA 프로세스

1. discover / discovery : DHCP 서버 찾기 = DHCP 클라이언트는 네트워크 및 데이터 링크 계층에서 브로드캐스트로 메시지를 전송하여 네트워크에서 DHCP 서버를 검색함.

2. offer : 후보 제안 = DHCP 서버는 클라이언트의 메시지를 수신하고 해당 클라이언트에게 IP 주소 후보 제공.

3. request : 선택 및 요청 = DHCP 클라이언트는 제공된 후보 중 IP 주소를 선택해서 DHCP 서버에 요청함.

4. Ack(Acknowledgement) : 확인 및 할당 = DHCP 서버에서 DHCP 클라이언트에 확인 전송 및 IP 할당 확정.

![DHCP 할당 과정 - 이미지 출처: https://brain.changhoi.kim/](https://changhoi.kim/images/2021-09-23-about-dhcp/03.png)

1단계를 제외하고 2-4단계의 패킷은 데이터 링크 계층에서 유니캐스트, 네트워크 계층에서 브로드캐스트로 전달함.

데이터 링크 계층 - 유니캐스트: DHCP 서버가 클라이언트에게 고유한 IP 주소와 설정 정보를 제공하는 목적이기 때문에, 해당 특정한 클라이언트에게만 정보를 전달해야 함.

네트워크 계층 - 브로드캐스트: DHCP 서버는 클라이언트의 IP 주소를 모르고, 클라이언트는 자신의 IP 주소를 할당받기 전에는 네트워크 상에서 식별이 어렵기 때문에 네트워크 내의 모든 디바이스에게 메시지를 전달하기 위한 효과적인 방법을 사용.

(전송 계층에서는 UDP 방식을 사용하기 때문에 port number는 불필요)

### DHCP 서버가 제공하는 정보 (Ack 단계)

1. IP 주소<br>
   : 클라이언트가 할당 받은 IP

2. first-hop 라우터 IP (게이트웨이 IP)<br>
   : 서브넷 외부로 통하는 게이트웨이 IP

3. DNS 서버 IP<br>
   : 로컬 네트워크 내 DNS 서버에 대한 정보

4. network mask (subnet mask)<br>
   : 서브넷 안에서는 브로드캐스트로 통신하기 때문에, 해당 서브넷의 구성원 수와 범위 등 기본적인 정보

---

### 참고 자료

[Microsoft - DHCP](https://learn.microsoft.com/ko-kr/windows-server/networking/technologies/dhcp/dhcp-top)

[RedHat - DHCP](https://access.redhat.com/documentation/ko-kr/red_hat_enterprise_linux/8/html/managing_networking_infrastructure_services/providing-dhcp-services_networking-infrastructure-services)
