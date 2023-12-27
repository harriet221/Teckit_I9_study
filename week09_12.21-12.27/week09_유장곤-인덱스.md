### 추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조

![](https://velog.velcdn.com/images/ujgon/post/565122c3-e067-4600-af99-ecbf4a77a9b5/image.png)

![](https://velog.velcdn.com/images/ujgon/post/7acdf670-8cc3-4f82-8b36-34b4203bad0c/image.png)


### 장점
---
- 테이블을 조회하는 속도와 그에 따른 성능을 향상시킬 수 있다.
- 전반적인 시스템의 부하를 줄일 수 있다.

### 단점
---
- 인덱스를 관리하기 위해 DB의 약 10%에 해당하는 저장공간이 필요하다.
- 인덱스를 관리하기 위해 추가 작업이 필요하다.
- 인덱스를 잘못 사용할 경우 오히려 성능이 저하되는 역효과가 발생할 수 있다.

### 인덱스를 사용하기 좋은 환경
---
규모가 작지 않은 테이블
INSERT, UPDATE, DELETE가 자주 발생하지 않는 컬럼
JOIN이나 WHERE 또는 ORDER BY에 자주 사용되는 컬럼
데이터의 중복도가 낮은 컬럼

### 인덱스 관리 방식
---

- ### B-Tree 자료구조
이진 탐색트리와 유사한 자료구조

 자식 노드를 둘이상 가질 수 있고 Balanced Tree 라는 특징이 있다 → 즉 탐색 연산에 있어 O(log N)의 시간복잡도를 갖는다.

 모든 노드들에 대해 값을 저장하고 있으며 포인터 역할을 동반한다.

- ### B+Tree 자료구조
 B-Tree를 개선한 형태의 자료구조
 모든 노드에 데이터(Value)를 저장했던 BTree와 다른 특성을 가지고 있다.

 값을 리프노드에만 저장하며 리프노드들 끼리는 링크드 리스트로 연결되어 있다 → 때문에 부등호문 연산에 대해 효과적이다.

 리프 노드를 제외한 노드들은 포인터의 역할만을 수행한다.

 BTree의 리프노드들을 LinkedList로 연결하여 순차검색을 용이하게 하는 등 BTree를 인덱스에 맞게 최적화 -> 데이터베이스 인덱스에서 가장 일반적으로 사용된다.

- ### HashTable 자료구조
 해시 함수를 이용해서 값을 인덱스로 변경 하여 관리하는 자료구조

 일반적인 경우 탐색, 삽입, 삭제 연산에 대해 O(1)의 시간 복잡도를 갖는다.

 
 해시 테이블은 Key값을 이용해 고유한 index를 생성하여 그 index에 저장된 값을 꺼내오는 구조로 다른 관리 방식에 비해 빠른 성능을 갖는다.
![](https://velog.velcdn.com/images/ujgon/post/ae85bf65-af9c-4dff-9fae-3b05344054a2/image.png)



 값 자체를 변경하기 때문에 부등호문(>,<), 포함문등의 연산에 사용할 수 없다.




출처)
https://mangkyu.tistory.com/96
https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Database/%5BDB%5D%20Index.md

