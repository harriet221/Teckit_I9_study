# Deadlock

Multi-programming 환경에서는 **여러 스레드(혹은 프로세스)가 한정된 수의 자원을 놓고 경쟁**할 수 있다.
스레드가 자원을 요청할 때, 해당 시점에 자원을 사용할 수 없으면 스레드는 대기 상태로 들어간다.
때로는 **둘 이상의 스레드가 다른 스레드가 점유하고 있는 자원을 사용하려고 무한 대기**에 빠질 수 있는데, 이런 상황을 **deadlock, 교착 상태**라고 한다.

---

# Deadlock 발생 조건

다음 네 가지 조건이 동시에 성립할 때 deadlock이 발생한다.

## Mutual Exclution(상호 배제)

**자원은 한 번에 하나의 프로세스만이 사용할 수 있어야 한다.** 사용 중인 자원을 다른 프로세스가 사용하려면 요청한 자원이 잠금 해제될 때까지 기다려야 한다.

## Hold and Wait(점유 대기)

최소한 **하나의 자원을 점유하고 있으면서** **다른 프로세스에 할당되어 사용하고 있는 자원을 추가로 점유하기 위해 대기**하는 프로세스가 있어야 한다.

## No Preemption(비선점)

다른 프로세스에 할당된 자원은 사용이 끝날 때까지 **강제로 빼앗을 수 없어야** 한다.

## Circular Wait(**순환 대기)**

프로세스의 집합 {P0, P1, ... , Pn}에서 P0는 P1이 점유한 자원을 대기하고 P1은 P2가 점유한 자원을 대기하고 ... Pn-1은 Pn이 점유한 자원을 대기하며 Pn은 P0가 점유한 자원을 요구해야 한다.
이렇게 **순환 형태로 자원을 대기**해야 한다.

---

# Deadlock 예방 및 회피

## Deadlock Prevention(예방)

네 가지 deadlock 발생 조건 중 하나만 제거해도 deadlock을 방지할 수 있다.

1. **Mutual Exclusion 부정**
    
    여러 개의 프로세스가 공유 자원을 사용할 수 있도록 한다.
    read-only 파일을 예로 들 수 있지만, 일반적으로는 자원의 특성 상 없앨 수 없는 조건이다.
    
2. **Hold and Wait 부정**
    
    프로세스가 실행되기 전에 필요한 모든 자원을 할당한다.
    이는 동적으로 자원을 요청하는 특성으로 인해 실용적이지 않다.
    
3. **No Preemption 부정**
    
    자원을 점유하고 있는 프로세스가 다른 자원을 요구할 때, 점유하고 있는 자원을 반납하고 요구한 자원을 사용하기 위해 기다리게 한다.
    
4. **Circular Wait 부정**
    
    자원에 고유한 번호를 할당하고, 번호 순서대로 자원을 요구하도록 한다.
    

## Deadlock 회피

Deadlock이 발생했을 때, 피하는 방법이다.

시스템의 프로세스들이 요청하는 **모든 자원을 교착상태를 발생시키지 않으면서 차레로 모두에게 할당**해 줄 수 있다면 **안정 상태**(safe state)에 있다고 말한다.

그리고 이처럼 특정한 순서로 프로세스들에게 자원을 할당, 실행, 종료 등의 작업을 할 때 **교착상태가 발생하지 않는 순서**를 찾을 수 있다면 이를 **안전 순서**(safe sequence)라고 부른다.

**불안정 상태**는 안정 상태가 아닌 상황, **교착상태가 발생할 가능성이 있는 상황**이다.
교착상태는 불안정 상태일 때 발생할 수 있다. (교착상태 ⊂ 불안정 상태)

**회피 알고리즘**은 **자원을 할당한 후에도 시스템이 항상 안전 상태에 있을 수 있도록 할당을 허용**하는 것이 기본 특징이다.

**은행원 알고리즘**(Banker's Algorithm)이 이러한 특징을 살린 대표적인 알고리즘이다.
은행원 알고리즘은 Dijkstra가 제안한 기법으로, 은행에서 모든 고객의 요구가 충족되도록 현금을 할당하는 데서 유래했다.
프로세스가 자원을 요구할 때 시스템은 자원을 할당한 후에도 안정 상태로 남아있게 되는지를 사전에 검사하여 교착상태를 회피하는 기법이다.
안정 상태에 있으면 자원을 할당하고, 그렇지 않으면 다른 프로세스들이 자원을 해지할 때까지 대기한다.

---

# Deadlock 탐지 및 회복

Deadlock을 허용한 다음에 회복하는 방법이다.

## Deadlock Detection(탐지)

- Resource-allocation graph(자원 할당 그래프)로 deadlock을 탐지할 수 있다.
    
    <img width="727" alt="스크린샷 2023-11-05 오후 4 52 09" src="https://github.com/jkeum-dev/Teckit_I9_study/assets/61774034/c3bcb6d3-0fa9-4a9e-86aa-459b52980fa5">
        
    프로세스 *Pi* 로부터 자원 *Rj* 로의 방향은 *Pi* → *Rj* 로 표현하며, 이는 프로세스 *Pi* 가 자원을 요청하는 것으로 현재 이 자원을 기다리는 상태이다.
    자원 *Rj* 로부터 프로세스 *Pi* 로의 방향은 *Rj* → *Pi* 로 표현하며, 이는 자원이 프로세스 *Pi* 에 할당된 것을 의미한다.
    

## Detection Recovery(회복)

Deadlock을 발생시킨 프로세스를 종료하거나 할당된 자원을 해제함으로써 회복한다.

1. 프로세스를 종료시키는 방법
    - Deadlock의 프로세스를 모두 중지시킨다.
    이 방법은 확실하게 deadlock cycle을 깨뜨릴 수 있지만, 비용이 많이 든다.
    - Deadlock cycle이 제거될 때까지 한 프로세스씩 중지시킨다.
    이 방법은 각 프로세스가 중단된 후에 deadlock 감지 알고리즘을 호출해야 하므로 상당한 오버헤드를 발생시킨다.
2. 자원을 선점하는 방법
    - 교착상태의 프로세스가 점유하고 있는 자원을 선점하여 다른 프로세스에게 할당하며, 해당 프로세스를 일시정지 시키는 방법이다.
    우선 순위가 낮은 프로세스, 수행된 횟수가 적은 프로세스 등을 위주로 프로세스의 자원을 선점한다.
