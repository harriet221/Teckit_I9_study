# 정규화(Normalization)

## 정규화
- 테이블 간 중복된 테이블을 최소화하기 위해 이용하는 기법
- 무결성 유지, 데이터 용량 최소화의 목적
- 제 1차, 2차, 3차, BCNF, 4차, 5차 순으로 이어지지만, 보통 3차 혹은 BCNF까지만 정규화가 이어짐

## 제 1정규화
- 도메인이 원자 값이어야 한다는 조건을 가진다.
- 기본키를 사용해 관련 데이터의 각 집합을 고유하게 식별할 수 있어야 함.
  ![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/1f8dccc2-f1a3-432a-b7f8-2a8dca15f27e)
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/ec1f6602-e955-4719-a587-bf183b7da269)

## 2차 정규화
- 부분적 함수 종속을 제거해야 한다.
- 복합 키(키1, 키2)를 가진 키가 둘 중 하나의 키가 다른 컬럼을 결정을 지어선 아니됨.
 ![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/398c2639-5ff5-41d0-af3f-c6b396fec621)
- 예를 들어 Manufacturer와 Model 키는 Model Full Name 을 결정하지만 복합 키 중 Manufacturer은 Manufacturer Country를 결정한다. 이 현상이 있으면 안됨

## 3차 정규화
- 이행적 함수 종석 제거를 함
- A키는 B키를 결정하지만 B키는 C키를 결정하는 방식을 허용하지 않음
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/28038433-011d-4796-8eb0-0b296f839aed)
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/2bb6c402-440a-41f7-880d-e222af8c9225)
- 한 테이블에 복합키가 우승자를 결정하지만 우승자는 생일을 결정하니 이행적 함수 종속이 일어난다. 그러므로 테이블 분해가 필요.

## BCNF(Boyce-codd Normal Form)
- 결정자이면서 후보키가 아닌 것을 제거해야 함
- 3차 정규화를 조금 더 강화한 버전
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/16f9dc71-5f5e-4b45-9ade-dbaa42226395)
- 학생과 과목은 학점을 결정 짓지만 교수는 과목을 결정하므로 분해가 필요
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/52760701-9dfa-4014-b6d4-70d04c27a74d)

## 그 외
### 1. 4차 정규화
- 다인 종속성 만족해야 함

### 2. 5차 정규화
- 조인 종속을 제거해야 함

### 3. 정규화 & 반정규화
- 정규화는 중복을 제거하기 위해 테이블을 분해함
- 반면 반정규화는 너무 많은 테이블끼리의 조인을 줄이기 위해 테이블 및 속성을 중복, 추가, 삭제를 진행함.
- 반정규화는 성능을 향상하기 위해 진행
