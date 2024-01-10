## Stream API의 특징
>- 원본 데이터를 변경하지 않음
>- 일회용
>- 내부 반복으로 작업을 처리

### 1. 원본 데이터를 변경하지 않음
- 별도의 요소들로 stream을 생성
#### 짝수만 필터링해서 출력 
``` java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> evenNumbers = numbers.stream()
                                    .filter(n -> n % 2 == 0)
                                    .collect(Collectors.toList());

System.out.println("Original numbers: " + numbers); // 원본 그대로 출력
System.out.println("Even numbers: " + evenNumbers); // 짝수로 필터링 된 결과 출력
```

### 2. 일회용 
``` java
// 스트림 생성
Stream<Integer> numberStream = numbers.stream(); 

// 첫 번째 사용
numberStream.forEach(System.out::println); 

// 두 번째 사용, 다시 사용하려고 하면 오류 발생
numberStream.forEach(System.out::println); 
```

### 3. 내부 반복 (Stream)
#### 두배 숫자 생성
```java
List<Integer> doubledNumbers = numbers.stream()
                                      .map(n -> n * 2)
                                      .collect(Collectors.toList());

System.out.println("Doubled numbers: " + doubledNumbers);
```
### 3-1. 외부 반복 (for, while 등 사용자가 직접 처리)
#### 두배 숫자 생성
```java
List<Integer> doubledNumbers = new ArrayList<>();

for (int i = 0; i < numbers.size(); i++) {
    Integer number = numbers.get(i);
    doubledNumbers.add(number * 2);
}

System.out.println("Doubled numbers: " + doubledNumbers);

```
---
### Stream 사용 전
``` java
String[] nameArr = {"IronMan", "Captain", "Hulk", "Thor"}
List<String> nameList = Arrays.asList(nameArr);

// 원본의 데이터가 직접 정렬됨
Arrays.sort(nameArr);
Collections.sort(nameList);

// 외부 반복
for (String str: nameArr) {
  System.out.println(str);
}

for (String str : nameList) {
  System.out.println(str);
}
```
### Stream 사용 후 
```java
// 원본의 데이터가 아닌 별도의 Stream을 생성함
Stream<String> nameStream = nameList.stream();
Stream<String> arrayStream = Arrays.stream(nameArr);

// 복사된 데이터를 정렬하여 출력함
nameStream.sorted().forEach(System.out::println);
arrayStream.sorted().forEach(System.out::println);
```
## Stream 연산 종류
>1. 생성하기
>2. 가공하기 (중간 연산)
>3. 결과 만들기 (최종 연산)

### 1. 생성하기
- Stream 객체를 생성하는 단계
- Stream은 재사용이 불가능하므로, 닫히면 다시 생성해야함

### 2. 가공하기 (중간 연산)
- 원본의 데이터를 별도의 데이터로 가공하기 위한 중간 연산
- 연산 결과를 Stream으로 다시 반환하기 때문에 연속해서 중간 연산을 이어갈 수 있음

>#### Stream 중간 연산
- filter(Predicate) - 조건에 맞는 요소만 포함하는 스트림을 반환
- distinct() - 중복된 요소를 제거
- limit(n) - 스트림의 처음부터 n개의 요소만 포함
- skip(n) - 스트림의 처음 n개 요소를 건너뜀
- map(Function) - 각 요소에 함수를 적용한 결과를 포함하는 스트림
- flatMap() - 각 요소를 스트림으로 변환하고, 하나의 스트림으로 합침

중간 연산은 모두 스트림을 반환한다.

### 3. 결과 만들기 (최종 연산)
- 가공된 데이터로부터 원하는 결과를 만들기 위한 최종 연산
- Stream의 요소들을 소모하면서 연산이 수행되기 때문에 1번만 처리가능

>#### Stream 최종 연산
- (boolean) allMatch(Predicate) - 모든 스트림 요소가 Predicate와 일치하는지 검사
- (boolean) anyMatch(Predicate) - 조건에 맞는 요소가 하나라도 있는지 검사
- (boolean) noneMatch(Predicate) - 모든 요소가 조건에 맞지 않는지 검사
- (Optional) findAny() - 스트림에서 임의의 요소를 반환
- (Optional) findFirst() - 스트림의 첫 번째 요소를 반환
- reduce() - 모든 요소를 처리하여 하나의 값으로 결합
- collect() - 스트림의 요소를 리스트, 맵, 세트 등의 컬렉션으로 변환
- (void) forEach() - 스트림의 각 요소에 대해 주어진 작업을 수행
- (Long) count - 스트림의 요소 개수 반환

출처 
- https://mangkyu.tistory.com/112
- https://github.com/gyoogle/tech-interview-for-developer/blob/master/Language/%5Bjava%5D%20Stream.md
