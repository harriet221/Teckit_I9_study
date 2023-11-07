> ## 배열 (array)
* **같은 타입(Type)**의 여러 변수들을 하나로 묶는 것
```java
arr[1(index)] = 4(elemnet);
```

**배열요소(element)** - 배열을 구성하는 각각의 값  
**인덱스(index)** - 배열에서 위치를 가리키는 숫자


> ## 배열의 선언, 생성
```java
선언
int [] arr;  // 타입 뒤 배열 선언
String arr[]; // 변수 뒤 배열 선언
```
```java
생성
arr1= new int[5]; // 변수 = new 타입[길이];
```
```java
선언과 생성
int arr1[] = new int[5]; // 타입 배열변수[] = new 타입[길이];
```

- 배열 선언 = 배열을 다루기 위한 참조변수를 위한 공간만 만들어지는 것
- 배열 생성 = 실제 값이 저장되는 공간 생성

> ## 배열 초기화
``` java 
int = 0;        // 기본값 
String = null;  // 기본값
```
```java
int arr = new arr[5]
arr[0] = 1; // 기본값 0 -> 1
int name = new name[5]
name[1] = hellow; // 기본값 null -> hellow
```
```java
int score[] = new int[]{ 50,60,70}; // 길이 생략 가능
int [] score = {50,60,70}; // 길이 생략 가능
score = new int[]{ 50, 60, 70}; // 길이 생략 가능
```


>## 배열 복사
* 배열은 한번 생성하면 길이를 변경할 수 없는 **상수**
* 배열 크기를 늘리기 위해 공간이 큰 배열을 만들고 복사
```java
System.arraycopy(arr1, 0, arr2, 0, arr1.length); 
// arr1의 index 0부터 arr1.length 전체 길이 만큼 arr2의 index 0 부터 붙여넣기.
```


>## 배열 정렬
 ```java
int numbers = [1, 5, 3, 2, 4];
// 배열 생성
numbers.sort();
or
numbers.sort((a, b) => a - b);
// 오름차순 정렬 [1, 2, 3, 4, 5]
numbers.sort((a, b) => b - a);
// 내림차순 정렬 [5, 4, 3, 2, 1]
// 문자열 배열 정렬
String strings = ["a", "b", "c", "d", "e"];
// 문자열 배열 정렬
strings.sort();
// 오름차순 정렬 ["a", "b", "c", "d", "e"]
strings.sort((a, b) => b.localeCompare(a));
// 내림차순 정렬 ["e", "d", "c", "b", "a"]
```

> ## 배열 비교 
```java
String[] arr1 = { "가", "나", "다"};
String[] arr2 = { "가", "나", "다"};
Arrays.equals(arr1, arr2)) 
// true
```
