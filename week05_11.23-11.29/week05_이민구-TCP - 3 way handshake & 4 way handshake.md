## TCP(Transmission Control Protocol) 란?
- 연결 지향형 프로토콜, 인터넷 신뢰성 보장

## 3 way handshake - 연결 성립

TCP는 정확한 전송을 보장해야 한다. 따라서 통신하기에 앞서, 논리적인 접속을 성립하기 위해 3 way handshake 과정을 진행한다.
![image](https://www.techopedia.com/wp-content/uploads/2023/03/ad900dc1-ad94-4c7b-a3f8-154ad27c35f1.png)

- SYN (synchronize sequence numbers) - 연결 확인을 위해 보내는 무작위의 숫자값 
 
- ACK (acknowledgements) - Client 혹은 Server로부터 받은 SYN에 1을 더해 SYN을 잘 받았다는 ACK 
 
- ISN (Initial sequence numbers) - Client와 Server가 각각 처음으로 생성한 SYN

이렇게 3번의 통신이 완료되면 연결이 성립된다. 


## 4 way handshake - 연결 해제

연결 성립 후, 모든 통신이 끝났다면 해제해야 한다.
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtQR1l%2FbtqyJRYdm3E%2F143elB5WCHDlofiAsax2J1%2Fimg.png)

1. 클라이언트는 서버에게 연결을 종료한다는 FIN 플래그를 보냄

2. 서버는 FIN을 받고, 확인했다는 ACK를 클라이언트에게 보냄 (이때 모든 데이터를 보내기 위해 CLOSE_WAIT 상태가 됨)

3. 데이터를 모두 보냈다면, 연결이 종료되었다는 FIN 플래그를 클라이언트에게 보냄

4. 클라이언트는 FIN을 받고, 확인했다는 ACK를 서버에게 보냄. (아직 서버로부터 받지 못한 데이터가 있을 수 있으므로 TIME_WAIT을 통해 기다린다.)
서버는 ACK를 받은 이후 소켓을 닫음 (Closed)
TIME_WAIT 시간이 끝나면 클라이언트도 닫음 (Closed)


이렇게 4번의 통신이 완료되면 연결이 해제

## 예상 질문 

[Q1] TCP의 연결 설정 과정(3단계)과 연결 종료 과정(4단계)이 단계가 차이나는 이유?
Client가 데이터 전송을 마쳤다고 하더라도 Server는 아직 보낼 데이터가 남아 있을 수 있기 때문에 일단 FIN에 대한 ACK만 보내고, 데이터를 모두 전송한 후에 자신도 FIN 메세지를 보내기 때문이라고 볼 수 있다.

[Q2] 만약 Server에서 FIN 플래그를 전송하기 전에 전송한 패킷이 Routing 지연이나 패킷 유실로 인한 재전송 등으로 인해 FIN 패킷보다 늦게 도착하는 상황이 발생하면 어떻게 될까?
위에서 4way handshake과정 마지막 부분에서 말한 TIME-WAIT을 말한 부분이 답이라고 보면되는데, TCP는 이러한 현상에 대비하여 Client는 Server로부터 FIN 플래그를 수신하더라도 일정시간동안 세션을 남겨놓고 잉여 패킷을 기다리는 과정을 거친다. 

[Q3] 초기 Sequence Number인 ISN을 0부터 시작하지 않고 난수를 생성해서 설정하는 이유?
Connection을 맺을 때 사용하는 포트(Port)는 유한 범위 내에서 사용하고 시간이 지남에 따라 재사용된다. 따라서 두 통신 호스트가 과거에 사용된 포트 번호 쌍을 사용하는 가능성이 존재한다. 서버 측에서는 패킷의 SYN을 보고 패킷을 구분하게 되는데 난수가 아닌 순처적인 Number가 전송된다면 이전의 Connection으로부터 오는 패킷으로 인식할 수 있다. 이런 문제가 발생할 가능성을 줄이기 위해서 난수로 ISN을 설정한다.

참고 및 출처 [블로그](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Network/TCP%203%20way%20handshake%20%26%204%20way%20handshake.md), [블로그](https://seongonion.tistory.com/74), [블로그](https://jeongkyun-it.tistory.com/180)
