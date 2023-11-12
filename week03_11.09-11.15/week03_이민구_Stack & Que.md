데이터를 저장하고 관리하는 방법 중 선형 자료구조의 두가지 
**스택과 큐** 에 대해서 알아보자.


## 스택(stack)이란
- 후입선출(LIFO, Last In First Out), 가장 나중에 들어온 것이 가장 먼저 나옴
- #### 데이터의 입력과 삭제는 맨 위 top에서 이루어짐
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbcgR9A%2FbtqSX70PCTe%2FdMSMQoJcZhDpq4sRRpu3A0%2Fimg.png)

> - push() - 데이터 넣음
- pop() - 데이터 최상위 값 뺌
- isEmpty() - 비었는지 확인
- isFull() - 꽉 찼는지 확인

**push와 pop**을 할 때 해당 위치를 알고 있어야 하므로 **스택 포인터(SP)**가 필요 
```java
private int sp = -1; // SP 기본 값 -1
```
## 사용시기
 - 함수의 콜스택 (호출과 복귀)
 - 후입선출 방식의 처리 (문자열 역순 출력) 
 - 후입선출 방식 알고리즘 (연산자 후위표기법, 괄호 검사, 팩토리얼 계산)
 - 깊이 우선 탐색 (DFS)
 
## 구현 방법
> - ### 배열
##### push
```java
public void push(Object o) {
    if(isFull(o)) {
        return;
        //스택 포인터가 최대 크기와 같으면 return
    }
    stack[++sp] = o;
    //아니면 스택의 최상위 위치에 값을 넣음
}
```
#### pop
```java
public Object pop() {
    if(isEmpty(sp)) {
        return null;
        //스택 포인터가 0이 되면 null로 return;
    }
    Object o = stack[sp--];
    //아니면 스택의 최상위 위치 값을 꺼내옴
    return o;
}
```
#### isEmpty
```java
private boolean isEmpty(int cnt) {
    return sp == -1 ? true : false;
    //입력 값이 최초 값과 같다면 true, 아니면 false
}
```
#### isFull
```java
private boolean isFull(int cnt) {
    return sp + 1 == MAX_SIZE ? true : false;
    //스택 포인터 값+1이 MAX_SIZE와 같으면 true, 아니면 false
}
```
- ### 동적 배열 스택
```java    
public void push(Object o) {
    if(isFull(sp)) {
        Object[] arr = new Object[MAX_SIZE * 2];
        // 기존 스택의 2배 크기만큼 임시 배열 arr 생성
        System.arraycopy(stack, 0, arr, 0, MAX_SIZE);
        // arraycopy로 stack의 인덱스 0부터 MAX_SIZE만큼 arr 배열의 0번째부터 복사
        stack = arr; 
        // arr 값을 stack에 저장
        MAX_SIZE *= 2; // 2배로 증가
    }
    stack[sp++] = o;
}
```

### 연결리스트와 배열 차이점 
#### 배열
 - 데이터를 배열에 저장
 - 빠른 접근 속도, 간단한 구현
 - 스택의 크기가 고정, 삽입과 삭제 시 배열의 크기를 조정 
#### 연결리스트 
 - 데이터를 노드에 저장
 - 스택 크기 제한 없음. 데이터 삽입, 삭제 자유로움
 - 느린 접근 속도, 복잡한 구현, 포인터의 추가 메모리 필요
 
## 큐(que)란
- 선입선출(FIFO, First In First Out), 가장 먼저 들어온 것이 가장 먼저 나옴
- 스택과 반대되는 개념
- #### 삽입은 맨 뒤 rear에서, 삭제는 front에서 이루어짐

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F5NOv1%2FbtqSTINnoq8%2F4f8bjzzf6W4POewlq8At31%2Fimg.png) 

enQueue() : 데이터 넣음
deQueue() : 데이터 뺌 
isEmpty() : 비어있는 지 확인
isFull() : 꽉 찼는 지 확인

데이터를 넣고 뺄 때 해당 값의 위치를 기억해야 함(스택 포인터 역할) 
이 위치를 기억하고 있는 게 front와 rear
front : deQueue(데이터를 뺄) 위치 기억
rear : enQueue(데이터를 넣을) 위치 기억

#### isFull
```java
public boolean isFull() {
    return (rear == queueSize-1);
}
// rear가 사이즈-1과 같아지면 가득찬 것
```
![image](https://github.com/ChanhuiSeok/ChanhuiSeok.github.io/blob/master/assets/img/sample/algo26_3.PNG?raw=true)
### 단점
- 선형 큐에서 삽입 및 삭제를 반복하다 보면, rear가 맨 마지막 인덱스를 가리키고, 앞에는 비어 있을 수 있지만 이를 꽉 찼다고 인식
(실제 데이터는 삭제 때마다 한 칸 앞으로 이동시키지 않았고, 인덱스 단위로 큐의 연산을 진행했기 때문)


이를 개선한 것이 
## 원형 큐
초기 front 와 rear는 맨 처음 인덱스(0)에 위치,
포화 상태를 쉽게 구분하기 위해 자리 하나를 항상 비워둠
(index + 1) % size로 순환시킨다

### 단점 
- 메모리 공간은 잘 활용하지만, 배열로 구현되어 있기 때문에 큐의 크기가 제한

이를 개선한 것이 
## 연결리스트 큐
크기 제한x, 삽입, 삭제 편리
### enqueue
```java
public void enqueue(E item) {
    Node oldlast = tail; // 기존의 tail 임시 저장
    tail = new Node; // 새로운 tail 생성
    tail.item = item;
    tail.next = null;
    if(isEmpty()) head = tail; // 큐가 비어있으면 head와 tail 모두 같은 노드 가리킴
    else oldlast.next = tail; // 비어있지 않으면 기존 tail의 next = 새로운 tail로 설정
}
```
### dequeue
```java
public T dequeue() {
    // 비어있으면
    if(isEmpty()) {
        tail = head;
        return null;
    }
    // 비어있지 않으면
    else {
        T item = head.item; // 빼낼 현재 front 값 저장
        head = head.next; // front를 다음 노드로 설정
        return item;
    }
}
```

## 사용시기
- 데이터의 순서대로 처리(은행 번호표, 프린터 출력 시)
- 너비 우선 탐색 (BFS)


## 고려사항
- 스택과 큐의 크기를 제한 할 것인지, 아닌지 (배열, 동적배열, 연결리스트)
- 데이터의 접근 속도가 중요한지, 삽입, 삭제가 중요한지 (배열, 연결리스트)
- 어떤 방식의 알고리즘이 필요한지 (스택 or 큐)
