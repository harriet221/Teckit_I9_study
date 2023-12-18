## JWT (JSON Web Token)
- 사용자 인증 및 정보 전송에 사용되는 방식
- JSON 객체에 인증에 필요한 정보들을 담은 후 비밀키로 서명한 토큰


## JWT Process

![](https://velog.velcdn.com/images/chuu1019/post/7f2c4d18-04f4-45aa-8fbf-6795f8afec81/image.png)
### 인증
1. 사용자 인증
- 사용자가 로그인하기 위해 서버에 로그인 요청
2. 토큰 생성
- 서버는 사용자의 신원과 권한 정보를 담은 JWT를 생성, 이때 JWT는 서버의 비밀 키로 서명
3. 토큰 전송
- 생성된 JWT는 사용자에게 전송
### 권한 부여
4. 토큰 사용
- 사용자는 서비스 요청 시 JWT를 함께 전송
5. 토큰 검증
- 서버는 받은 JWT의 서명을 검증하여, 요청이 유효한지 판단
6. 응답 처리 JWT 검증 후, 서버는 요청에 대한 적절한 응답을 제공

## 권한 확인 간 JWT를 계속 보내는 이유
### HTTP의 특성
- ``connectionless`` : 한 번 통신이 이뤄지고 난 후 연결이 바로 끊어짐
- ``Stateless`` : 이전 상태를 유지/기억하지 않음

## JWT 구성
### 헤더(Header)
- typ와 alg 두가지의 정보를 지니고 있음 
- typ는 토큰의 타입을 지정합니다. JWT이기에 "JWT"라는 값이 들어감
- alg : 해싱 알고리즘을 지정합니다. 기본적으로 HMAC, SHA256, RSA가 사용되면 토큰을 검증 할 때 사용되는 signature부분에서 사용
### 정보(Payload)
- 정보의 한 조각인 클레임(claim)을 포함
- 등록된 클레임
  - 서비스에서 필요한 정보들이 아닌, 토큰에 대한 정보들을 담기위하여 이름이 이미 정해진 클레임
  -  발급자(iss), 주제(sub), 수신자(aud) 등  
- 공개 클레임
  - 충돌을 방지하기 위해 IANA JSON Web Token 등록되거나, URI 형식의 이름을 사용
- 개인 클레임 
  - 클라이언트와 서버 간의 협의 하에 사용되는 사용자 정의 클레임
  - 특정 사용 사례에 맞춰 정보를 전달하는 데 사용

### 서명(Signature)
- 헤더의 인코딩된 값, 페이로드의 인코딩된 값, 비밀 키를 해시 알고리즘으로 서명하여 생성
- 이 서명은 토큰이 변경되지 않았음을 검증하고, 메시지의 발신자가 누구인지 확인하는 데 사용

[출처 1](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Web/JWT(JSON%20Web%20Token).md), [출처 2](https://velog.io/@jihwankim94/Server-JWT-Json-Web-Token-란)
