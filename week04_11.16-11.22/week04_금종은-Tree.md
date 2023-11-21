# 트리(Tree)

노드들이 나무 가지처럼 연결된 비선형 계층적 자료구조

<img width="25%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/a7491bae-4651-40e7-a91d-639e92a686d8">


## 트리 구조에서 사용되는 용어

<img width="60%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/9e6cbd4f-ca6a-47a3-af53-6f8b0eafb57b">

<img width="30%" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/f53140ff-894a-4a1d-bebb-875e76859cdb">

- 노드(Node)
    - 트리를 구성하고 있는 기본 요소
    - 노드에는 키와 하위 노드에 대한 포인터를 가지고 있음
- 간선(Edge)
    - 노드와 노드를 연결하는 선
- 루트 노드(Root Node)
    - 트리 구조에서 부모 노드가 없는 최상위 노드
- 부모 노드(Parent Node)
    - 자식 노드의 상위 노드
- 자식 노드(Child Node)
    - 부모 노드의 하위 노드
- 형제 노드(Sibling Node)
    - 같은 부모를 가지는 노드
- 리프 노드(Leaf Node)
    - 자식 노드가 없는 노드
    - 외부 노드(External Node, Outer Node) 혹은 단말 노드(Terminal Node)라고도 함
- 가지 노드(Branch Node)
    - 자식 노드를 하나 이상 가진 노드
    - 내부 노드(Internal Node, Inner Node) 혹은 비단말 노드(Non-terminal Node)라고도 함
- 깊이(Depth)
    - 루트에서 어떤 노드까지의 간선 수
    - 루트 노드의 깊이: 0
    - D 노드의 깊이: 2
- 높이(Height)
    - 어떤 노드에서 리프 노드까지 가장 긴 경로의 간선 수
    - 리프 노드의 높이: 0
    - A 노드의 높이: 3
- 레벨(Level)
    - 같은 깊이를 가지고 있는 노드를 묶어서 레벨로 표현
- 차수(Degree)
    - 각 노드가 지닌 가지의 수(자식 노드의 수)
    - 리프 노드의 차수: 0
    - A 노드의 차수: 2
- 경로(Path)
    - 한 노드에서 다른 노드에 이르는 길 사이에 놓여있는 노드의 순서
    - A - H 경로: A-B-D-H
    - 경로의 길이(Path Length): 해당 경로에 있는 총 노드의 수
- 크기(Size)
    - 자신을 포함한 자손 노드 수
    - B 노드의 크기: 6

## 트리의 특징

- 하나의 루트 노드와 0개 이상의 하위 트리로 구성되어 있음
- 데이터를 순차적으로 저장하지 않으므로 비선형 자료구조임
- 트리 안에 또 다른 트리가 있는 재귀적 자료주고임
- 순환 구조를 가지지 않으며, 서로 연결된 무방향 그래프 구조임
- 노드 간에 부모-자식 관계를 가지는 계층형 자료구조이며, 모든 자식 노드는 하나의 부모 노드만을 가짐
- 노드가 `n`개인 트리는 항상 `n-1`개의 간선을 가짐

## 트리 순회 방식

<img src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/4dc13cc2-8035-4286-b73f-708a04cc1d58">

1. 전위 순회(Pre-order)
    - 각 부모 노드를 순차적으로 먼저 방문하는 방식
    - 부모 노드 → 왼쪽 자식 노드 → 오른쪽 자식 노드
    - 1 → 2 → 4→ 8 → 9 → 5 → 10 → 11 → 3 → 6 → 13 → 7 → 14
2. 중위 순회(In-order)
    - 왼쪽 하위 트리를 방문한 후에 부모 노드를 방문하는 방식
    - 왼쪽 자식 노드 → 부모 노드 → 오른쪽 자식 노드
    - 8 → 4 → 9 → 2 → 10 → 5 → 11 → 1 → 6 → 13 → 3 → 14 → 7
3. 후위 순회(Post-order)
    - 왼쪽 하위 트리부터 하위를 모두 방문한 후에 부모 노드를 방문하는 방식
    - 왼쪽 자식 노드 → 오른쪽 자식 노드 → 부모 노드
    - 8 → 9 → 4 → 10 → 11 → 5 → 2 → 13 → 6 → 14 → 7 → 3 → 1
4. 레벨 순회(Level-order)
    - 부모 노드부터 계층별로 방문하는 방식
    - 1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9 → 10 → 11 → 13 → 14

</br>

> 참고 자료</br>
[Tistory | yoongrammer - [자료구조] 트리 (Tree)](https://yoongrammer.tistory.com/68)</br>
[gyoogle/tech-interview-for-developer/Computer Science/Data Structure/Tree.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Tree.md)
