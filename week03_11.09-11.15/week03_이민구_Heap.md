#### 힙은 우선 순위 큐를 위하여 만들어진 자료구조 

- 스택 : 가장 최근 데이터
- 큐 : 가장 먼저 들어온 데이터
- **우선순위 큐 : 가장 우선순위가 높은 데이터**

> **우선순위 큐**는 배열, 연결리스트, 힙으로 구현 가능하며, **힙(heap)**으로 구현하는 것이 가장 효율적

- 힙은 완전 이진 트리의 일종으로, 여러 개의 값들 중에 최댓값이나 최소 값을 빠르게 찾아내도록 만들어진 자료구조
- 반정렬 상태(느슨한 정렬 상태)를 유지, 큰 값이 상위 레벨에 있고, 작은 값이 하위 레벨에 있다는 정도
- 힙 트리에서 중복된 값을 허용 (이진 탐색 트리에서는 중복 허용 x)

## 힙의 종류
### 최대 힙 (Max Heap)
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FyXt2a%2Fbtq7ddSvksp%2FabjtbzX0kb5mbKWHgS84d1%2Fimg.png)

- 부모 키 값이 자식노드 키 값보다 **큰 힙**
- 가장 큰 값이 루트 노드에 있음

### 최소 힙 (Min Heap)
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FLulip%2Fbtq66t3mygU%2FXhwpPwIBf7gl580EV5cLa0%2Fimg.png)
- 부모 키 값이 자식노드 키 값보다 **작은 힙**
- 가장 작은 값이 루트 노드에 있음

## 힙 표현
- 힙은 완전 이진트리로 일반적으로 배열로 표현
- 개발 편의성과 가독성 때문에 배열 인덱스 1부터 사용
- 특정 위치의 노드 번호는 새로운 노드가 추가되어도 변하지 않음

### 힙에서의 부모 노드와 자식 노드의 관계
왼쪽 자식의 인덱스 = (부모의 인덱스) x 2
오른쪽 자식의 인덱스 = (부모의 인덱스) x 2 + 1
부모의 인덱스 = (자식의 인덱스) / 2


![image](https://gmlwjd9405.github.io/images/data-structure-heap/heap-index-parent-child.png)

### 힙의 삽입

- 힙에 새로운 요소가 들어오면, 일단 새로운 노드를 힙의 마지막 노드에 삽입
- 새로운 노드를 부모 노드들과 교환
![image](https://gmlwjd9405.github.io/images/data-structure-heap/maxheap-insertion.png)
### 힙의 삭제

- 최대 힙에서 최대값은 루트 노드이므로 루트 노드가 삭제됨 (최대 힙에서 삭제 연산은 최대값 요소를 삭제하는 것)
- 삭제된 루트 노드에는 힙의 마지막 노드를 가져옴
- 힙을 재구성
![image](https://gmlwjd9405.github.io/images/data-structure-heap/maxheap-delete.png)

[참고자료_1](https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html) / [참고자료_2](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Heap.md) / [참고자료_3](https://yoongrammer.tistory.com/80)
