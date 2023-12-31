페이지 교체 알고리즘은 컴퓨터 운영체제에서 메모리 관리를 위해 사용되는 알고리즘 중 하나입니다. 주로 가상 메모리 시스템에서 사용되며, 주기억장치(RAM)가 꽉 찼을 때 어떤 페이지를 교체할지 결정하는 방법을 정의합니다.

가장 널리 사용되는 페이지 교체 알고리즘은 다음과 같습니다:

- LRU (Least Recently Used):
가장 최근에 사용되지 않은 페이지를 교체합니다. 시간적으로 가장 오래 전에 접근된 페이지를 교체하는 방식입니다.
![image](https://github.com/ujgon/git_study/assets/125572887/4d8a05df-ec02-4cc9-9646-2266265969e0)

- FIFO (First-In-First-Out):
가장 먼저 메모리에 올라온 페이지를 먼저 교체합니다. 큐 구조로 동작하여 먼저 들어온 페이지가 먼저 나가게 됩니다.
하지만 맨 위에 있는 페이지가 자주 사용되는 페이지일 수도 있다.
무조건 오래된 페이지가 대상이 되기 때문에 성능이 떨어질 수 있다.
![image](https://github.com/ujgon/git_study/assets/125572887/ffb8ee6b-d9ff-47fb-9357-b8206de22436)

- OPT (Optimal Algorithm) : 최적 페이지 교체 알고리즘
이상적인 상황에서 가장 적합한 페이지를 교체합니다. 알고리즘은 앞으로 사용되지 않을 페이지를 교체하는 것이 최선일 것으로 예측하여 실행합니다. 
앞으로 사용하지 않을 페이지를 교체.
미래의 메모리 접근 패턴을 파악해 대상 페이지를 결정하는것.
하지만 이 알고리즘은 실제로 구현하기 어려운 경우가 많습니다.(사실상 불가)
![image](https://github.com/ujgon/git_study/assets/125572887/54f0cb06-b39c-4042-9e4b-c92a5e1a99b6)

- LFU (Least Frequently Used):
가장 적게 사용된 페이지를 교체합니다. 사용 빈도가 가장 낮은 페이지를 교체하는 방식입니다.
페이지가 몇 번 사용되었는지를 기준으로 봄.

	FIFO 알고리즘보다 성능은 우수하지만 페이지 접근 횟수(빈도)를 추가로 표시해야하기 때문에, 메모리 낭비 단점이 있다.
![image](https://github.com/ujgon/git_study/assets/125572887/ab4c6601-8f66-4b25-82b7-fb57bd1c7863)


- 그 외 MFU(Most Frequently User) 알고리즘 : 참조 횟수가 가장 많은 것을 교체하는 알고리즘
NUR(Not Used Rencently) 알고리즘 : 추가 비트 2개만 사용하여 미래를 추정 등이 있다.

-
이러한 알고리즘들은 각자의 장단점이 있으며, 어떤 알고리즘이 시스템에 최적인지는 상황에 따라 다를 수 있습니다. 페이지 교체 알고리즘은 메모리 관리의 효율성과 성능에 많은 영향을 미치므로, 특정한 시스템이나 환경에 적합한 알고리즘을 선택하는 것이 중요합니다.


ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
출처:
https://sommda.tistory.com/67
https://code-lab1.tistory.com/60#google_vignette