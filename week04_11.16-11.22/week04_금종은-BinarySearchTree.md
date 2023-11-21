# 이진 트리(Binary Tree)

- 자식 노드가 최대 두 개인 노드들로 구성된 트리
- 자료의 삽입 및 삭제 방법에 따라 나뉨
    - 정 이진 트리(Full Binary Tree): 각 노드가 0개 혹은 2개의 자식 노드를 가짐
    - 완전 이진 트리(Complete Binary Tree): 마지막 레벨을 제외한 모든 노드가 가득 차 있어야 하고, 마지막 레벨의 노드는 전부 차 있진 않아도 되지만 왼쪽은 채워져 있어야 함
    - 포화 이진 트리(Perfect Binary Tree): 정 이진 트리이면서 완전 이진 트리인 경우로, 모든 리프 노드의 레벨이 동일하면서 모든 레벨이 가득 차 있는 트리
    
    <img width="80%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/0b9bc736-8ecb-4bbe-acf9-51d19c8d3ecb">


# 이진 탐색 트리(Binary Search Tree)

- 이진 탐색(Binary Search)에 연결 리스트(Linked List)를 결합한 이진 트리

- 이진 탐색의 효율적인 탐색 능력을 유지하면서 빈번한 자료 입력과 삭제를 가능하게 고안된 트리
  - 이진 탐색에서 탐색에 소요되는 시간복잡도 O(logN). 삽입 및 삭제 불가
  - 연결 리스트에서 삽입 삭제의 시간복잡도 O(1), 탐색의 시간복잡도 O(N)

## 특징

- 중복된 키를 허용하지 않음
- 노드의 왼쪽 서브 트리는 해당 노드의 키보다 작은 키를 갖는 노드들로 이루어져야 함
- 노드의 오른쪽 서브 트리는 해당 노드의 키보다 큰 키를 갖는 노드들로 이루어져야 함
- 하위 트리도 이진 탐색 트리여야 함

<img width="50%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/208247ab-86ea-440d-863f-f596616986b4">

- 이진 탐색 트리의 순회는 중위순회 방식을 따르며, 정렬된 순서로 읽을 수 있음
- 탐색에 대한 시간복잡도는 균형 상태일 때 O(logN), 불균형 상태일 때 최대 O(N)
    <img width="70%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/19bc0d9b-d0fb-42ba-9a44-89a5404eb43b">
    

## 생성 예시

<img width="85%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/a16bd3e9-a804-4327-bc96-031b19aca76e">

1. 50을 트리의 루트 노드로 삽입함
2. 15가 50보다 작으므로 왼쪽 자식 노드로 삽입
3. 62가 50보다 크므로 오른쪽 자식 노드로 삽입

## 연산

### 검색(Search)

BST에서 특정 요소의 위치를 찾음

1. 루트 노드에서 시작
2. 검색할 값을 루트 노드의 값과 비교함. 루트보다 작으면 왼쪽에 대하여 재귀, 크면 오른쪽에 대해 재귀
3. 일치하는 값을 찾을 때까지 반복
4. 찾는 값이 없으면 null 반환

<img width="75%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/597aa8bb-1e12-439b-9214-1aaa90d8c612">

### 삽입(Insert)

BST에 새 노드를 삽입하는 작업으로, 새 데이터는 항상 리프 노드로 삽입됨

1. 루트 노드에서 시작
2. 삽입할 값을 루트 노드의 값과 비교함. 루트 노드보다 작으면 왼쪽에 대하여 재귀, 크면 오른쪽에 대하여 재귀
3. 리프 노드에 도달했을 때 해당 노드보다 작으면 왼쪽에 삽입, 크면 오른쪽에 삽입

<img width="75%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/8e59e28b-5918-46b6-b645-cadc2236648c">

### 삭제(Delete)

BST에서 특정 노드를 삭제하는 작업으로, 세 가지 상황이 있음

1. 삭제할 노드가 리프 노드인 경우
    
    단순히 노드를 삭제하면 됨
    
    <img width="75%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/38352bc6-bfca-4267-bc8c-d7616795fb28">
    
2. 삭제할 노드에 자식이 하나만 있는 경우
    
    노드를 삭제하고 자식 노드를 삭제된 노드의 부모 노드에 직접 연결
    
    <img src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/db5b4b0d-85f1-43f3-80ed-120d1078462d">
    
3. 삭제할 노드에 자식 노드가 두 개 있는 경우
    
    successor 노드를 찾는 과정이 필요(오른쪽 하위 트리에서 최소값/중위 순회에서 다음 노드)
    
    1. 삭제할 노드를 찾음
    2. 삭제할 노드의 successor 노드를 찾음
    3. 삭제할 노드와 successor 노드의 값을 바꿈
    4. successor 노드 삭제
    
    <img src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/35eca0bc-b6d8-4af6-9615-72b7dbe6bf6f">
    
</br>

> 참고 자료</br>
[Tistory | yoongrammer - [자료구조] 이진 탐색 트리 (BST, Binary Search Tree)](https://yoongrammer.tistory.com/71)</br>
[Velog | @yeonkr - [자료구조] 이진 트리와 이진 탐색 트리 (BST: Binary Search Tree)](https://velog.io/@yeonkr/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%9D%B4%EC%A7%84-%ED%8A%B8%EB%A6%AC%EC%99%80-%EC%9D%B4%EC%A7%84-%ED%83%90%EC%83%89-%ED%8A%B8%EB%A6%AC-BST-Binary-Search-Tree)</br>
[gyoogle/tech-interview-for-developer/Computer Science/Data Structure/Binary Search Tree.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Binary%20Search%20Tree.md)
