### 트랜잭션 (Transaction) : 업무 처리의 논리적인 단위
---

### 트랜잭션 격리수준 (Transaction Isolation Level)
---
동시에 여러 트랜잭션이 수행될 때, 트랜잭션끼리 얼마나 격리시키는지 나타내는 것.
실행 중인 트랜젹션의 중간결과를 다른 트랜잭션이 접근하지 못하도록 막는 것.
ANSI/ISO SQL 표준 (SQL92)에서 정의한 4가지 트랜잭션 격리성 수준은 아래와 같다.

![](https://velog.velcdn.com/images/ujgon/post/01f63384-69c8-48d2-ad39-c51b17a29b24/image.png)
사진 출처 : DBGuide.net
![](https://velog.velcdn.com/images/ujgon/post/3ea8648e-974e-4906-abb7-79d4ed27ba34/image.png)

### Read Uncommitted(커밋되지 않은 읽기)
---
- 트랜잭션에서 아직 커밋되지 않은 데이터를 다른 트랜잭션이 읽는 것을 허용.
- 각 트랜잭션에서의 변경 내용이 COMMIT이나 ROLLBACK 여부에 상관 없이 다른 트랜잭션에서 값을 읽을 수 있다.
- DIRTY READ 발생
(트랜잭션이 작업이 완료되지 않았는데도 다른 트랜잭션에서 볼 수 있게 되는 현상)

### Read Committed(커밋된 읽기)
---
- 트랜 잭션에서 커밋이 확정된 내용만 다른 트랜잭션이 읽는 것을 허용
- Dirty Read 방지할 수 있으나 Non-Repeatable Read와 Phantom Read 현상은 못 막음
(읽는 시점에 따라 결과가 다를 수 있다는 의미)


### Repeatable Read(반복 가능한 읽기)
---
- 자신의 트랜잭션이 생성되기 이전의 트랜잭션에서 COMMIT 이 된 데이터만 읽는다.
- MySQL과 MariaDB 가 기본으로 사용하는 격리 수준
- MySQL에서는 트랜잭션마다 트랜잭션 ID를 부여하여 트랜잭션 ID보다 작은 트랜잭션 번호에서 변경한 것만 읽게 된다.
- 트랜잭션이 이루어지는 동안 일관성 있는 데이터를 보장
- 첫 번째 쿼리에 있던 레코드가 사라지거나 값이 바뀌는 현상을 방지함
- 첫 번째 쿼리에 없던 레코드가 생기는 Phantom Read는 막지 못 함 
  (다른 트랜잭션에서 수행한 변경 작업에 의해 레코드가 보였다가 안 보였다가 하는 현상)

### Serialize Read(직렬화 가능)
---
- 트랜잭션이 이루어지는 동안, 새로운 레코드가 생기거나 사라지거나 값이 바뀌는 현상을 방지함
-  Non-Repeatable Read와 Phantom Read를 방지함
- 가장 단순한 격리 수준이지만 가장 엄격한 격리 수준
- 데이터를 접근할 때, 항상 Lock을 걸고 데이터를 조회
- 성능 문제로 데이터베이스에서 거의 사용되지 않는다.


### 격리수준 선택 고려사항
---
트랜잭션 격리수준에 대한 변경은 동시성/데이터 무결성과 연관되어 있다.
동시성을 증가시키면 데이터 무결성에 문제가 발생하고, 데이터 무결성을 유지하면 동시성이 떨어지게 된다.
트랜잭션 격리수준이 높을 수록 데이터 무결성 및 정합성이 높아지나, 동시성(성능)은 낮아지게 된다.
반대로 격리수준이 낮을 수록 동시성(성능)은 높아지나, 데이터 정합성이 깨지는 여러 부정합문제가 발생할 수 있다.
각 서비스에 특성에 맞게 적절한 격리수준을 선택하여 사용하여야 한다.


---
출처)
https://thenaeul.wordpress.com/2020/12/19/db-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B2%A9%EB%A6%AC%EC%88%98%EC%A4%80-transaction-isolation-level/
https://velog.io/@yujiniii/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B2%A9%EB%A6%AC-%EC%88%98%EC%A4%80
https://hahahoho5915.tistory.com/68