# Auth 
- Authentication 혹은 Authentication + Authorization 를 의미

## Authentication (= AuthN, 인증)
- 로그인과 같이 사용자 또는 프로세스의 신원을 확인하는 프로세스
- 이 과정에서 사용자는 자격 증명(비밀번호 등)을 제공하고, 이는 이미 저장된 데이터와 비교

### Authentication Factors (인증 요소)
1. 지식 기반
   - 사용자만 알고 있는 정보(예: 비밀번호, 이름).
2. 소유 기반
   - 사용자가 소유한 물건을 이용한 인증(예: OTP, 휴대폰 SMS 인증).
3. 속성 기반
   - 사용자의 생체적 특징을 이용한 인증(예: 지문, 홍채).

- One Factor 인증
  - 하나의 인증 요소만 사용.
- Two Factor 인증
  - ``두 가지 다른 인증 요소``의 조합을 사용.
- MFA(Multi Factor Authentication)
  - 여러 인증 요소를 결합한 방식.

### Authentication Techniques (인증 기술)
1. **비밀번호 기반 인증**
   - 전통적인 비밀번호 사용
2. **비밀번호없는 인증**
   - 매직 링크나 OTP를 통해 비밀번호 없이 인증
3. **2FA / MFA**
   - 추가 보안을 위해 여러 인증 요소 사용
4. **Single Sign-On (SSO)**
   - 하나의 자격 증명으로 여러 응용 프로그램에 접근
5. **Social Authentication**
   - 소셜 네트워크 계정을 통한 인증
6. **API Authentication**
   - API 키나 토큰을 사용한 인증
7. **생체 인증**
   - 사용자의 생체적 특징을 사용한 인증

## Authorization (= AuthZ, 권한 부여)
- 사용자가 특정 자원에 대해 어떤 작업을 할 수 있는지를 결정하는 규칙과 절차
- 파일이나 데이터와 같은 시스템 리소스에 대한 액세스 수준을 결정하는 보안 메커니즘

### Authorization Techniques (권한부여 기술)
1. **API keys**
    - 사용자가 시스템에 대한 인증된 액세스 권한을 얻기 위해 사용하는 긴 문자열로, 주로 API 호출 시 식별 수단으로 사용
3. **HMAC (Hash-Based Message Authentication Code)**
    - 암호화 해시 기능과 비밀 암호화 키를 사용하여 데이터 무결성과 메시지 신뢰성을 동시에 검증
4. **JWT (JSON Web Token)**
    - 당사자 간에 안전하게 데이터를 전송하기 위한 공개 표준으로, 사용자는 공개/개인 키 쌍을 사용하여 권한을 부여 받음
5. **SAML (Security Assurance Markup Language)**
    - XML 기반의 인증 및 권한 부여 시스템으로, SSO(싱글 사인온) 형식을 사용
6. **OpenID**
    - 인증 서버의 인증을 기반으로 사용자 신원을 확인하는 데 사용되며, REST와 유사한 기본 프로필 정보를 제공
7. **OAuth**
      - 사용자가 비밀번호를 제공하지 않고도 자신의 정보에 대한 접근 권한을 타사 웹사이트나 애플리케이션에 부여할 수 있는 개방형 표준

# 마무리
## Authentication (인증)
### 목적
- 사용자 또는 프로세스의 신원을 확인하는 것
### 방법
- 사용자가 자격 증명(비밀번호, OTP, 생체 인식 등)을 제공하며, 시스템은 이를 저장된 데이터와 비교
### 유형
- 비밀번호 기반, 2FA/MFA, 비밀번호 없는 인증, SSO, Social Authentication, API 인증, 생체 인증 등
## Authorization (권한부여)
### 목적
- 사용자가 시스템 내에서 수행할 수 있는 작업의 범위를 결정하는 것
### 방법 
- 시스템이 사용자의 역할이나 그룹을 기반으로 리소스에 대한 접근 권한을 설정
### 유형 
- 역할 기반 액세스 제어(RBAC), JSON 웹 토큰(JWT), SAML, OpenID, OAuth 등

인증은 ``사용자가 누구인지``를 확인하는 과정이고, 
권한부여는 ``사용자가 무엇을 할 수 있는지``를 정하는 과정

#### 출처
- https://baek.dev/post/24/
