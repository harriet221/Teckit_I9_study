## 해시
---
해시(hash)란 다양한 길이를 가진 데이터를 고정된 길이를 가진 데이터로 매핑(mapping)한 값이다. 
이를 이용해 특정한 배열의 인덱스나 위치나 위치를 입력하고자 하는 데이터의 값을 이용해 저장하거나 찾을 수 있다. 
기존에 사용했던 자료 구조들은 탐색이나 삽입에 선형시간이 걸리기도 했던것에 비해, 해시를 이용하면 즉시 저장하거나 찾고자 하는 위치를 참조할 수 있으므로 더욱 빠른 속도로 처리할 수 있다. 해시값이라고도 한다.
![](https://velog.velcdn.com/images/ujgon/post/67726585-c792-4c39-a3c2-09113f92617b/image.png)


## 특징
---
### 1. 무결성
- 해시는 특정한 데이터를 이를 상징하는 더 짧은 길이의 데이터로 변환하는 행위를 의미한다. 
- 여기서 상징 데이터는 원래의 데이터가 조금만 달라져도 확연하게 달라지는 특성을 가지고 있어 무결성을 지키는 데에 많은 도움을 준다. 

예를 들어 '한국'이라는 문자열의 해시와 '한귝'라는 문자의 해시 결과값은 완전히 다른 문자열이 나오게 된다 

### 2. 보안성
- 해시는 기본적으로 복호화(간단히, 부호된 데이터를 사람이 읽을 수 있는 형태로 되돌리는것) 가 불가능하다는 특징이 있다. 
- 입력 데이터 집합이 출력 데이터 집합을 포함하고 있으므로, 특정한 출력 데이터를 토대로 입력 데이터를 찾을수 없기 때문이다. 

- 동일한 출력 값을 만들어낼 수 있는 입력 값의 가짓수는 수학적으로 무한개라고 볼 수 있다.  해시는 애초에 복호화를 수행할 수 없도록 설계되었으며, 실제로도 해커가 쉽게 복호화를 할 수 없다는 점에서 강한 보안성을 가진다

### 3. 해시레이트
- 해시레이트란 연산 처리능력을 측정하는 단위로 해시 속도를 의미한다. 
일반적으로 해시레이트가 높아져 연산량이 많아질 경우, 더 빠른 채굴이 이루어지기 때문에 채굴 난이도가 높아진다. 
- 초당 해시값 계산 횟수의 총합으로 암호화폐의 연산 작용 과정에서 얻을 수 있는 채굴의 성공 확률과 실제로 채굴에 성공한 시간으로부터 도출되는 이론값이라고도 할 수 있는데, 이는 채굴 간격과 난이도와는 달리 네트워크에서 직접 측정되지는 않는다. 
- 채굴 난이도와 같은 정방향의 값을 가져서 채굴 난이도가 높아진다는 의미는 해시레이트가 저하된다는 것이고, 이는 곧 단위 시간당 생산할 수 있는 채굴량이 줄어든다는 의미이다. 

 현재 비트코인의 채굴은 제네시스마이닝이나 해시플레어와 같이 대규모 하드웨어, 즉 채굴기를 보유한 사람들에 의해 이루어지고 있다. 



## 활용
---
- 해시는 블록체인과 IPFS( 분산 파일 시스템에 데이터를 저장하고 공유하기 위한 프로토콜, 하이퍼미디어, 파일 공유 P2P 네트워크) 등 다양한 분야에서 활용되고 있다. 

- 보안 분야에서도 널리 사용되는데 이는 해시 함수가 원래의 문장을 복호화할 수 없게 뭉개버린다는 장점과 원문과 해시값 사이에 선형적 관계가 없다는 특성을 지니고 있기 때문. 

 해시 함수의 결과물은 고정된 길이의 숫자이므로, 원래의 정보는 손실되는데, 이러한 특성 때문에 하나의 원 데이터는 하나의 해시값만 가지지만, 하나의 해시값을 만들어 낼 수 있는 원본 데이터는 매우 많아서, 해시값만 가지고는 원문을 복원해해는 것은 불가능하다. 

 따라서 비밀번호, 전자서명, 전자투표, 전자상거래와 같은 민감한 입력의 무결성을 검증할 때 주로 사용된다. 

### 해시 함수(hash function)
해시 함수는 임의의 길이를 갖는 임의의 데이터에 대해 고정된 길이의 데이터로 매핑하는 함수를 말한다. 
이러한 해시 함수를 적용하여 나온 고정된 길이의 값을 해시값이라고 한다. 
보통 그리 복잡하지 않은 알고리즘으로 구현되기 때문에, 상대적으로 CPU, 메모리 같은 시스템 자원을 덜 소모하는 특성이 있다. 
그리고 해시함수는 결정론적으로 작동하기 때문에, 원래의 데이터가 같으면 해시값도 항상 동일하며, 이 출력값은 가능한 한 고른 범위에 균일하게 분포하는 특성이 있다. 
이러한 특성으로 인해 다양한 목적에 맞게 설계된 해시 함수가 존재하며 자료구조, 캐시, 중복 레코드 검색, 유사 레코드 검색, 에러검출 등 다양한 분야에서 매우 유용하게 사용된다. 
하지만 서로 다른 데이터가 동일한 해시값을 가질 수 있기 때문에 해시충돌이 발생할 수 있다. 
대표적인 해시 함수로는 MD5, SHA 등이 있다.

![](https://velog.velcdn.com/images/ujgon/post/a16fe99d-7c80-4fe1-adee-8eaf57494542/image.png)


### 해시 테이블(hash table)
해시 테이블은 키와 값을 매핑해 둔 데이터 구조이다. 
해시함수를 이용하여 검색하고자 하는 값을 변환하면 그 값이 저장된 위치를 즉시 알아낼 수 있다. 데이터의 양이 아무리 많아지더라도 원리적으로 해시 변환과 검색에 걸리는 시간은 항상 동일하다. 따라서 방대한 데이터에서 특정한 값을 검색할 때 해시 테이블을 사용하면 검색 시간을 획기적으로 단축할 수 있다. 
해시 맵(hash map)은 기존 해시 테이블의 기능을 개선한 신 버전의 해시 테이블이다.



### 해시 방법(hashing)
해싱이란 해시함수를 사용하여 주어진 값을 변환한 뒤, 해시 테이블에 저장하고 검색하는 기법을 말한다. 
해싱에 사용되는 자료구조는 배열(array)과 연결리스트(linked list)가 조합된 형태이다. 
짧은 해시 키를 사용하여 항목을 찾으면, 원래의 값을 이용하여 찾는 것보다 더 빠르기 때문에, 해싱은 데이터베이스 내의 항목들을 색인하고 검색하는데 사용된다. 

해싱은 데이터들을 저장하거나 찾을 때 인덱스(index)라는 또다른 데이터 스트럭쳐를 이용하는 대신, 각 데이터들이 테이블의 어느 영역에 위치할 것인가를 결정해주는 해시함수를 사용하여 일정한 시간 내에 데이터들을 효과적으로 찾을 수 있도록 해주는 것이다. 

따라서 데이터들은 순차적으로 저장되는 것이 아니라 테이블 전 영역에 걸쳐서 골고루 분포하게 되며, 저장된 데이터를 찾을 때에도 해시함수를 사용하면 곧바로 그 위치를 알아내는 것이 가능하기 때문에 매우 빠른 속도로 데이터를 검색할 수가 있게 된다.





---
출처_
http://wiki.hash.kr/index.php/%ED%95%B4%EC%8B%9C#cite_note-4
https://velog.io/@acacia__u/%ED%95%B4%EC%8B%9C%ED%95%A8%EC%88%98