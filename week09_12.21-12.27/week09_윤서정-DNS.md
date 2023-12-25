# DNS

## 1. DNS(Domain Name System)

: 사용자에게 친숙한 문자로 이루어진 도메인(호스트) 네임과 컴퓨터에게 익숙한 32bits IP(네트워크) 주소가 상호 매핑된 시스템

전 세계의 (공인) IP 주소와 그에 대응하는 도메인 네임을 효율적으로 관리하기 위해 개발된 방식으로, 다양한 도메인 등록 업체를 통해 등록 가능.
그러나 각 IP 주소는 모두 고유한 도메인과 매핑되어야 하기 때문에 엄격한 생성 규칙을 따르고 있으며, 결과적으로는 ICANN(Internet Corporation for Assigned Names and Numbers, 국제인터넷주소관리기구)에서 (다른 root DNS 서버 담당 기구들과 함께) 총체적으로 관리함.

<br>

## 2. Domain Name

도메인 네임은 DNS의 효율성을 높이기 위해 bottom to top 방식을 취함. 따라서 마지막 도메인(최상위 도메인)부터 해석.

#### 도메인 단계

- 1단계 도메인 / 최상위도메인 (TLD, Top Level Doamin) : 일반최상위도메인(gTLD; .com, .org, .net)과 국가최상위도메인(ccTLD; .us, .uk, .kr)로 구분됨.
- 2단계 도메인 / 차상위 도메인 (SLD, Second Level Domailn) : 필수X, 기관 종류(정부/교육/비영리 등)를 표시하는 등 도메인 등록자의 아이덴티티가 구체화되는 부분.
- 하위 도메인 / 서브 도메인 : 필수X, 필요에 따라 다른 하위/서브 도메인 추가 가능. (www)

![Domain tree](https://www.cloudflare.com/img/learning/dns/glossary/dns-root-server/dns-root-server.png)

<br>

## 3. DNS 서버

: 클라이언트로부터 도메인 이름에 대한 조회 요청을 받고, 해당 도메인 이름에 대한 IP 주소를 찾아서 클라이언트에 응답하는 서버.

#### DNS 서버 유형

- **권한 DNS 서버(Authoritative DNS Server)**: 도메인 이름에 대한 IP 주소를 저장하고 있는 DNS 서버 (DB 역할)
- **정보 제공 DNS 서버(Recursive DNS Server)**: 권한 DNS 서버로부터 도메인 이름에 대한 IP 주소를 조회하여 클라이언트에 응답하는 DNS 서버 (대부분의 DNS 서버)

#### DNS 서버 데이터베이스

DNS 서버의 데이터베이스는 계층형 구조를 가짐. (계층형 분산 데이터베이스 구조)

→ 인터넷상의 모든 도메인 서버는 ".(dot)" 또는 루트(root)라 불리는 도메인 서버 아래에 역트리(Inverted tree)구조로 계층적으로 구성되어 있음.

root DNS 서버 : 최상위 레벨 도메인에 대한 IP 주소 담당. (A - M 전 세계 13대 X / 13개 root DNS IP O)

<br>

## 4. DNS 서버 동작 흐름

#### 클라이언트 ↔ DNS 서버

1. (클라이언트) DNS 서버에 도메인 이름에 대한 조회를 요청
2. (DNS 서버) 조회 요청에 포함된 도메인 이름을 분석
3. (DNS 서버) 자신의 데이터베이스에서 해당 도메인 이름에 대한 IP 주소 탐색
4. (DNS 서버) 해당 IP 주소를 클라이언트에게 응답

#### DNS 서버 간

"www.naver.com"

1. 최상위 도메인 "com" - 루트 DNS 서버에서 "com"이라는 도메인 네임에 대한 IP 주소를 가지고 있는 권한 DNS 서버 탐색
2. 중간 도메인 "naver" - 권한 DNS 서버 통해 "com"에 대한 IP 주소 획득. 이를 사용하여 다음 단계인 중간 도메인 "naver" 해석(IP 주소화)
3. 하위 도메인 "www" - 최종적으로 하위 도메인인 "www" 해석(IP 주소화)

#### DNS name resolution

클라이언트의 요청에 따라 DNS 서버들은 서로 정보를 공유하고 캐싱하여 전체 시스템의 성능을 향상시킴. DNS는 계층적 구조로 설계되어 있어, 채택적 / 재귀적 두 해석을 결합하여 효율적이고 신속하게 동작함.

- 채택적 해석 (Iterative Resolution):

클라이언트가 DNS 쿼리를 DNS 서버에 보내면, DNS 서버는 이 쿼리에 대한 답을 알고 있을 때까지 다른 DNS 서버에게 쿼리를 전달함. 클라이언트가 원하는 정보를 얻을 때까지 지속되며, 최종적으로 목표로 하는 DNS 서버는 요청에 대한 답을 제공하거나 해당 정보가 없을 경우 에러를 반환함.

> local → root → local → TLD → local → 권한 DNS 서버 → local 흐름을 거치는 iterated query 방식

- 재귀적 해석 (Recursive Resolution):

클라이언트가 DNS 서버에게 쿼리를 보내면, DNS 서버는 필요한 경우 자신이 아는 정보를 사용하여 계속해서 하위 DNS 서버에 쿼리를 전송함. 이 프로세스는 루트 DNS 서버에서 시작하여 최종적으로 목표로 하는 DNS 서버에서 적절한 응답을 얻을 때까지 계속되며, 클라이언트는 최종적으로 원하는 정보나 오류 메시지를 받게 됨.

> local → root → TLD → 권한 DNS 서버 → local의 순차적인 흐름을 거치는 reculsive query 방식

#### 종합하면,

사용자가 웹 브라우저에 도메인 네임을 입력하면, 먼저 로컬 DNS 서버를 통해 루트 DNS 서버에 해당 도메인 네임의 최상위 레벨 도메인에 대한 IP 주소를 요청하게 됨. 루트 DNS 서버는 해당 IP 주소를 응답함. 사용자의 컴퓨터는 해당 IP 주소를 사용하여 다음 단계의 DNS 서버에 연결 및 요청. 이 단계의 DNS 서버는 다음 레벨 도메인에 대한 IP 주소를 응답함. 이 과정을 반복하여 사용자는 전체 도메인 네임에 대한 IP 주소를 획득하게 됨.

---

### 참고

- [한량개발자 티스토리](https://ijbgo.tistory.com/27#recentComments)
- [cloudflare](https://www.cloudflare.com/ko-kr/learning/dns/glossary/dns-root-server/)
