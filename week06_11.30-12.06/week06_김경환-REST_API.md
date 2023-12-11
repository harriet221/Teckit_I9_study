# REST API (Representational State Transfer)

## 유저 인터페이스(User Interface)

사용자가 어떤 기계의 기능들을 활용할 수 있도록 만든 제어장치

### 유저 인터페이스의 예

- TV의 스크린, 모니터

- 스크롤바, 슬라이더, 브라우저 창

## API(Application Programming Interface)

사용자와 기계가 UI를 통해 명령을 주고 받듯이 소프트웨어가 다른 소프트웨어를 활용할 수 있도록 만든 형식

지정된 형식을 통해 요청, 명령을 받을 수 있다

## REST API

서버에 데이터를 요청하거나 입력할 때 개발자들 사이에서 널리 쓰이는 일종의 형식

과거 SOAP란 형식을 대체

사용하는 프로그래밍 언어나 프레임워크에 구애 받지 않는다.

## REST API의 이점

- 각 요청이 어떤 동작이나 정보를 위한 것인지 그 요청의 모습 자체로 추론 가능

    - 서비스는 혼자 만드는 것이 아니기 때문에 이 부분은 굉장한 이점

    - 다른 개발자들도 쉽게 일을 인계 받거나 이 API를 통해 다른 제품을 만들 개발자들에게 큰 편의를 제공
​

RESTful하게 만든 API는 요청을 보내는 주소만으로도 요청의 의도를 파악이 가능


예시)

### https://(도메인)/classes/2/students

classes = 학원의 반들 목록 요청

2 = 반의 정보

students = 반에 해당하는 학생의 정보

​

자원을 구조와 함께 나타내는 이런 식의 구분자를 URI라고 한다

위 예와 같은 조회작업과 정보를 새로 넣거나 수정하거나 삭제하는 작업을 통틀어 CRUD라고한다.

Create 생성

Read 조회

Update 수정

Delete 삭제


## REST API의 사용

서버에 REST API로 요청 보낼 때는 HTTP(Hyper Text Transfer Protocol)라는 규약에 따라 신호 요청

우체국을 이용할 때도 일반우편 등기 택배 등 다양한 방식이 있듯이 HTTP로 요청을 보낼 떄도 다양한 메소드(방법)이 있다

> GET - (read) 데이터 조회
>
> POST - (create) 새로운 정보 추가
>
> DELETE - (delete) 삭제
>
> PUT - (update) 수정 (정보를 통째로 갈아 끼울 때)
>
> PATCH - (update) 수정 (특정 정보를 변경할 때)
​
## REST API란?

HTTP에서 제공하는 메소드에는 GET, POST, DELETE, PUT, PATCH 등이 있습니다. 이들의 기능은 제한되어 있지 않아 각각으로 서로의 동작을 구현할 수 있습니다. 하지만 RESTful한 API를 만들기 위해서는 목적에 따라 구분해서 사용해야 합니다.

이렇듯 HTTP 요청을 보낼때 어떤 url에 어떤 메소드를 사용할지 개발자들 사이에 널리 지켜지는 약속을 REST API라고 합니다.

<sub> 참고 문헌 : https://www.youtube.com/watch?v=iOueE9AXDQQ&t=42s&ab_channel=%EC%96%84%ED%8C%8D%ED%95%9C%EC%BD%94%EB%94%A9%EC%82%AC%EC%A0%84</sub>