>## 연결리스트(linked list)
- 각 노드가 데이터와 포인터를 가지고 한 줄(선형)로 연결되어 있는 것
- 포인터가 다음의 노드를 연결
![연결리스트](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbygm8v%2Fbtq5lxMb2f7%2FUookpU9dnl1uKNZs6i4Bu0%2Fimg.png)

## 배열과 차이점
- 배열은 index를 사용, 연결리스트는 노드를 사용 
- 배열의 크기는 고정, 크기 변경을 위한 많은 비용이 소모(새로운 배열을 만들고, 기존 데이터를 복사) 
연결리스트 동적 크기, 삽입, 삭제 용이

## 연결리스트 단점 
- 임의 액세스 허용 x, 첫번째 노드부터 순차적으로 액세스
- 배열에 비해 많은 메모리 필요, 포인터의 여분의 메모리 공간이 목록의 각 요소에 필요

> ## 선언
```java
LinkedList li = new LinkedList(); 
// 타입 설정x, Object로 입력
LinkedList<LinkedListDemo> demo = new LinkedList<LinkedListDemo>(); 
// List타입을 LinkedListDemo
LinkedList<Integer> i = new LinkedList<Integer>(); 
// int 타입으로 선언
LinkedList<Integer> i2 = new LinkedList<>(); 
// 타입 선언 생략도 가능
LinkedList<Integer> i3 = new LinkedList<Integer>(Arrays.asList(1, 2, 3)); 
// 초기 값 세팅		
LinkedList<String> s = new LinkedList<String>(); 
// String 타입 사용
LinkedList<Character> ch = new LinkedList<Character>(); 
// Char 타입 사용
```

> ## 데이터 추가
```java
ll.add("Hello"); // (object) add linkedlist 마지막 데이터 추가
ll.add("Welcome"); 
ll.add(1, "World"); // (index, object), 데이터 위치 지정
// 실행결과 ( Hello, world, Welcome)
```

> ## 데이터 수정 
```java
ll.set(1, "City");
// 실행결과 ( Hello, City, Welcome)
```

> ## 데이터 삭제
```java
ll.removeFirst(); // 첫 번째 데이터 삭제
ll.removeLast(); // 마지막 데이터 삭제
ll.remove(); // remove로 삭제하면 첫 번째 데이터를 삭제
ll.remove(2); // Index 순번의 데이터를 삭제
ll.clear(); // List의 모든 데이터를 삭제
```

> ## 데이터 저장
```java
ll.get(1) // Index 순번의 데이터를 불러옴
```
