# Main Memory

## Address Binding

![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/a71ec882-0c41-4376-b20c-8c5ff19ccc5e)

- 프로그램은 바이너리 실행 파일로 디스크에 상주

  ■ 실행하려면 프로그램을 메모리에 가져와야 함

  ■ 프로세스의 00000000 으로 시작하지 않음
- 소스의 주소는 일반적으로 기호
- 컴파일러는 일반적으로 바인드

  ■ 재배치 가능한 주소에 대한 기호 주소
- 링커나 로더는 차례로 바인드

  ■ 절대 주소로 재배치 가능한 주소

## Logical & Physical Address Space

![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/1aa6d5ae-812a-4b27-a4b3-e1881ece7cfa)


- Logical Address : Cpu에 의해 생성된 주소
- Physical Address : 메모리 장치에 의해 인식되는 주소, 즉, 메모리 주소 레지스터에 로드되는 주소를 의미
- Logical Address Space : 사용자 프로그램에 의해 생성되는 모든 논리적 주소들의 집합
- Physical Address Space : 논리적 주소들에 매핑되는 모든 물리적 주소들의 집

## Protection of memory space

![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/6b3dc234-c929-4013-bc93-0f34f5f3006d)

- 주소는 base 보다 커야 적재 가능
- 주소는 base + limit 보다 작아야 적재 가능
- 만일 둘 다 부합하지 않다면 적재하기 좋지 않은 주소이므로 OS에 trap 걸리도록 설정

## MMU(Memory ManageMent Unit)

![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/3f850bb6-10e4-4140-85f0-ed11a53230f4)

- 논리적인 주소를 물리적인 주소로 적재할 수 있도록 매핑하는 중간 역할
- relocation register 를 사용

## Dynamic Loading

- 더 나은 메모리 공간 활용도를 얻기 위해 이용
  
  ■ 루틴은 호출될 때까지 로드되지 않음
- 동적 적재 장점
  
  ■ 루틴은 필요할 때만 로드
  
  ■ 원하는 루틴을 로드하기 위해 재배치 가능한 링크 로더가 호출
  
  ■ 그리고 이 변경 사항을 반영하도록 프로그램의 주소 테이블을 업데이트

## Contigous Memory Allocation

![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/9b503f9f-94b5-4482-9149-6a3afa6b2ef2)


- 가장 효율적인 방법으로 메인 메모리를 할당해야 함
- 주소 공간을 여러개로 분할하지 않고 물리적 메모리의 한 곳에 연속적으로 적재

## Problem of Dynamic Storage Allocation

- 새로운 프로그램을 적재시키기 위해서 가용공간 중 어떤 위치에 올릴 것인지 결정하는 문제 발생
- First-fit : 데이터 순서대로 메인 메모리에 적재
- Best-fit : 데이터 크기가 메인 메모리 크기와 오차가 별로 없는 곳에 적재
- Worst-fit : 데이터가 메인 메모리에 적재할 때 오차가 많이 남을 때

## Fragmentation

- 외부 단편화
  
![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/a23c679d-ba96-4b5e-a559-dc3579b5b453)
  
  ■ 남아있는 총 메모리 공간이 요청한 메모리 공간보다 크지만 남아있는 공간이 연속적이지 않아 발생하는 현상

- 내부 단편화

![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/bf6acd55-65b2-48f4-b3dd-228b914b14b1)

  ■ 메인 메모리 내 사용자 영역이 실행 프로그램보다 커서 프로그램의 사용 공간을 할당 한 후 사용되지 않고 남게되는 현상

## Paging

- 외부 단편화의 해결 방법으로, 주소를 불연속적으로 할당하는 메모리 관리 구조
- 페이징에서 자주 등장하는 용어 두 가지 : Page / Frame

> Page : 가상 메모리를 일정한 크기로 나눈 블록 / Frame : 물리 메모리를 일정한 크기로 나눈 블

## Swapping

- 메모리에 있는 데이터를 디스크에 있는 데이터와 바꾸는 작업
- swap out : 메모리에서 디스크로 내보내는 것
- swap in : 디스크에서 메모리로 올리는 것

# 학습 출처
https://yonghwankim-dev.tistory.com/484

https://baebalja.tistory.com/416

https://www.inflearn.com/course/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C-%EA%B3%B5%EB%A3%A1%EC%B1%85-%EC%A0%84%EA%B3%B5%EA%B0%95%EC%9D%98#reviews
