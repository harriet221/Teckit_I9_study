# Join

## Join이란?
- 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 방법
- 전에 알아봤던 key에서 서로 공통된 속성의 연결을 이용해 데이터를 검색

## Join종류

### Inner Join
- 교집합을 뜻, 두 테이블 간 공통된 속성을 추출
- From절에서 Join을 이용함
<p align="center">
  <img src="https://velog.velcdn.com/images/dnu05043/post/fb6255f9-8fb7-474d-bd1d-d59a5177eb05/image.png"/>
</p> 

```sql
SELECT *
FROM dept D INNER JOIN emp E
ON D.속성1 = E.속성1;
```

### Left Outer Join
- 왼쪽 테이블을 기준 삼아 왼쪽 테이블과 다른 테이블과 조인한 중복된 값을 추출
<p align="center">
  <img src="https://velog.velcdn.com/images/dnu05043/post/e6d558c7-da9c-447f-b142-e6c87b00ea15/image.png"/>
</p> 

```sql
SELECT 속성명 FROM 테이블1 LEFT OUTER JOIN 테이블2
ON 테이블1.속성 = 테이블2.속성;

SELECT 속성명 
FROM 테이블1,테이블2
WHERE 테이블1.속성 = 테이블2.속성(+);
```

### Right Outer Join
- 오른쪽 테이블을 기준으로 삼아 오른쪽 테이블과 다른 테이블과 조인한 중복된 값 추출

<p align="center">
  <img src="https://velog.velcdn.com/images/dnu05043/post/ee5063ef-2b73-4f68-b52e-faa6f9366e39/image.png"/>
</p>

```sql
SELECT 속성명 FROM 테이블1 Right OUTER JOIN 테이블2
ON 테이블1.속성 = 테이블2.속성;

SELECT 속성명 
FROM 테이블1,테이블2
WHERE 테이블1.속성(+) = 테이블2.속성;
```

### Full Outer Join
- 조인한 두 테이블 전체를 의미, 합집합

![](https://velog.velcdn.com/images/dnu05043/post/11483af4-9737-4a19-bfac-4d746606957f/image.png)
```sql
SELECT 속성명 
FROM 테이블1 FULL OUTER JOIN 테이블2 
ON 테이블1.속성 = 테이블2.속성;

SELECT 속성명 
FROM 테이블1,테이블2
WHERE 테이블1.속성 = 테이블2.속성;
```

### CROSS JOIN
- 모든 경우의 수 표현, 일반 집합 연산자 중 카티션 프로덕트(X) 생각하면 된다.
![](https://velog.velcdn.com/images/dnu05043/post/d9b0d0e1-cc13-481c-a6b3-82262e657092/image.png)
```sql
SELECT 속성명
FROM 테이블1,테이블2;

SECECT 속성명
FROM 테이블1 CROSS JOIN 테이블2;
```

### Self Join
- 자기 자신을 회귀(Regression)하는 것을 의미

![](https://velog.velcdn.com/images/dnu05043/post/677147d3-f221-4c8f-9327-ef9c5a88cd1d/image.png)

```sql
SELECT 속성명 
FROM 테이블1 A JOIN 테이블1 B 
ON A.속성 = B.속성;
```
