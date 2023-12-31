## 메모리 관리 기법
---

다중 프로그래밍 시스템에서 복수의 프로세스를 주메모리에 수용하기 위해 
주메모리를 동적 분할하는 메모리 관리 작업.

크게 두가지로 나뉨.

### 1. 연속 메모리 관리
---
프로그램 전체가 하나의 커다란 공간에 연속적으로 할당되어야 한다.
(프로그램 전체가 메모리에 연속적으로 할당.）

* 고정 분할 기법 : 메모리가 고정된 파티션으로 분할. ー＞내부 단편화 발생

* 동적 분할 기법 : 파티션들이 동적으로 생성되고 자신의 크기과 같은 파티션 메모리 할당 -> 외부 단편화 발생

### 단편화?
기억 장치의 빈 공간 또는 자료가 여러 조각으로 나뉘는 현상.

* 내부 단편화
고정된 파티션보다 작은 프로세스 조각이 할당될 경우, 빈공간이 발생하는 현상
![image](https://github.com/ujgon/git_study/assets/125572887/3f10d982-b553-4910-85d6-1f5956a94e18)

* 외부 단편화
남아있는 메모리의 크기가 실행하고자 하는 프로세스보다 크지만, 연속적이지 않은 공간에 존재하여 실행하지 못하는 현상 
![image](https://github.com/ujgon/git_study/assets/125572887/e31a7619-97f2-48de-a9cf-aa281cecc3fa)

####  연속 메모리 관리에서 단편화를 줄이는 할당 방식
1. 최초 적합 (First Fit) : 가장 처음 만나는 빈 메모리 공간에 프로세스를 할당
2. 최적 적합 (Best Fit) : 빈 메모리 공간의 크기와 프로세스의 크기 차이가 가장 적게 나는 곳에 할당.
3. 최악 적합 (Worst Fit) : 빈 메모리 공간의 크기와 프로세스 크기 차이가 가장 크게 나는 곳에 할당한 후 빈 공간에 또 다른 프로세스를 할당할 수 있을 것이라는 가정하에 수행.








### 2. 불연속 메모리 기법
---
* 프로그램의 일부가 서로 다른 주소 공간에 할당될 수 있는 기법

	

페이징(paging)
---
* 프로세스의 주소 공간을 일정한 크기의 페이지로 분할하여 메모리에 ‘불연속’으로 적재하는 방식.
-페이지 : 고정 사이즈의 가상 메모리 내 프로세스 조각 - 고정크기
-프레임 : 페이지 크기와 같다. 메모리를 고정된 크기로 나눈 블록

하나의 프로세스가 사용하는 메모리 공간이 연속적이어야 한다는 제약을 없애는 메모리 관리 방법이다.

![image](https://github.com/ujgon/git_study/assets/125572887/b5e58588-aa4a-454a-9b4c-9c51f316664e)

* 페이징 기법은 고정 분할 방식을 이용한 가상 메모리 관리 기법이다.

* 물리 주소 공간을 같은 크기로 나누어 사용한다.

* 페이지 size == 프레임 size

* 모든 프로세스는 하나의 페이징 테이블을 가진다.


* 장점 :
논리 메모리는 물리 메모리에 저장될 때 연속되어 저장될 필요가 없음
물리 메모리에 남는 프레임에 적절히 배치되기 때문에 외부 단편화가 생기지 않음

* 단점 : 
내부 단편화 문제가 발생
페이지 단위를 매우 작게 만들면 내부 단편화를 줄일 수 있지만 페이지 매핑 과정이 복잡해져 오히려 비효율적




세그먼테이션(Segmentation)
---
* 물리적인 고정 크기로 분할하는 페이징과 달리 프로그램의 논리적인 내용 단위로 프로세스의 메모리 공간을 분리하는 기법
즉, 프로세스를 크기가 서로 다른 논리적인 단위인 세그먼트로 분할 해 메모리에 적재하는 방법.
(세그먼트 : 서로 다른 크기의 논리적 블록이 연속적 공간에 배치되는 것 - 가변크기)

![image](https://github.com/ujgon/git_study/assets/125572887/bd514482-8ec4-4cea-b455-f01322d3c7e6)

* 세그멘테이션 테이블에는 세그먼트의 크기를 나타내는 limit과 물리 메모리 상의 시작 주소를 나타내는 adress가있다.

* 프로세스의 크기에 따라 메모리를 분할하기 때문에 매핑 테이블에 크기 정보를 포함한다.

* 세그먼테이션의 장점
가변적인 크기를 가지기 때문에 내부 단편화 문제가 해소됨
보호와 공유 기능을 수행할 수 있음. 프로그램의 중요한 부분과 중요하지 않은 부분을 분리하여 저장할 수 있고, 같은 코드 영역은 한번에 저장 가능
 

* 세그먼테이션의 단점
외부 단편화 문제가 발생



페이징,세그먼테이션의 종류
---


* 단순 페이징 : 
각 프로세스는 프레임들과 같은 길이를 가진 균등 페이지로 나뉨.
		외부 단편화 X
		소량의 내부 단편화 존재

*  단순 세그먼테이션 : 
각 프로세스는 여러 세그먼트들로 나뉨.
	내부 단편화 X, 메모리 사용 효율 개선, 동적 분할을 통한 오버헤드 감소
	외부 단편화 존재


*  가상 메모리 페이징
단순 페이징과 비교해 프로세스 페이지 전부를 로드시킬 필요X
필요한 페이지가 있으면 나중에 자동으로 불러들어짐
외부 단편화 X
복잡한 메모리 관리로 오버헤드 발생


*  가상 메모리 세그먼테이션
필요하지 않은 세그먼트들은 로드되지 않음
필요한 세그먼트 있을때 나중에 자동으로 불러들어짐
내부 단편화X










ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ



출처 : https://velog.io/@narangke3/%EA%B0%80%EC%83%81%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%B0%8F-%ED%8E%98%EC%9D%B4%EC%A7%95-%EC%84%B8%EA%B7%B8%EB%A9%98%ED%85%8C%EC%9D%B4%EC%85%98-%EA%B8%B0%EB%B2%95

https://steady-coding.tistory.com/524

https://velog.io/@tlsdnxkr/CS-%EB%8B%A8%ED%8E%B8%ED%99%94-%EC%84%B8%EA%B7%B8%EB%A9%98%ED%85%8C%EC%9D%B4%EC%85%98-%ED%8E%98%EC%9D%B4%EC%A7%95%EB%82%B4%EB%B6%80%EB%8B%A8%ED%8E%B8%ED%99%94-%EC%99%B8%EB%B6%80%EB%8B%A8%ED%8E%B8%ED%99%94



