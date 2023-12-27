- 데이터를 데이터그램 단위로 처리하는 프로토콜
-> 데이터그램 : 독립적인 관계를 지니는 패킷
- 신뢰할 수 없는, 비연결형 프로토콜 
- Transport layer 계층

### 특징
- 정보를 주고 받을 때 신호절차를 거치지 않음.
- UDP 헤더의 CheckSum 필드를 통해 최소한의 오류만 검출
- #### TCP보다 쉽고 빠름


#### TCP는 신뢰성 있는 데이터 전송을 위해, UDP는 속도와 효율성을 위해 개발

### UDP 프로토콜 사용 서비스 
- streaming multimedia apps
VoIP, 온라인 게임, 비디오 스트리밍등 사용
- DNS
DNS는 request와 response가 매우 간결하게 끝나므로, TCP같은 프로토콜을 사용하면 오히려 부담이 큼, 중간에 패킷이 손실되더라도, 통신과정이 간결하므로 그냥 다시 보내면 됨
- SNMP (Simple Network Management Protocol)
네트워크상의 장치들을 점검할 때 쓰는 프로토콜로, 주기적으로 물어보는 형태이기 때문에 간결한 UDP를 사용


>### TCP header
![](https://velog.velcdn.com/images%2Fcoral2cola%2Fpost%2Ff2d2a271-b6b4-4f31-8700-016a3d41aefb%2Fimage.png)
### UDP header
![](https://mblogthumb-phinf.pstatic.net/MjAxOTA4MzFfMjY2/MDAxNTY3MjI2MTk5NDU3.75B8JoP-6HSvzCaR3O3HtuQIF7Bg9GRt1JumKJ-mDAcg.1VFOfZ_ujkBAWoaQPcAV9n2mBjJNfNbcDDP2Lis9ILMg.PNG.6yujin6/3.png?type=w800)
- TCP의 헤더에 비해 굉장히 간결
- source와 destination의 포트가 적혀있고, UDP 패킷의 길이, checksum 값이 포함되어 있으며, 나머지는 다 payload (데이터)

참고
- https://ddongwon.tistory.com/83
