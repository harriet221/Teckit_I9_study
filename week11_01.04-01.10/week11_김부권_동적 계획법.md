# 동적 계획법 (Dynamic Programming)

## 동적 계획법이란?
- 기본적인 아이디어로 하나의 큰 문제를 여러 개의 작은 문제로 나누어서 그 결과를 저장해 다시 큰 문제를 해결할 때 사용하는 것으로 특정한 알고리즘이 아닌 하나의 문제해결 패러다임으로 볼 수 있음
- 큰 문제를 작은 문제로 쪼개 그 답을 저장해두고 재활용 한다해서 '기억하며 풀기'라고 불리기도 함

## 동적 계획법 조건
- 동적 계획밥을 적용하기 위해선 두 가지 조건을 만족시켜야 함
- 부분 반복 문제 (Overlapping Subproblem)
  ![image](https://github.com/harriet221/Teckit_I9_study/assets/148305892/6a5749b4-aa97-41d7-af41-b58a144ed251)

👉 항상 새로운 부분문제를 생성해내기 보단 계속해서 같은 부분 문제가 여러 번 재사용되거나 재귀 알고리즘을 통해 해결

👉 fibo 3~5 들이 이미 진행했던 연산임에도 불구하고 반복적으로 연산

- 최적 부분 구조 (Optimal Substructure)
 ```java
  fibo[i] = fibo[i-1] + fibo[i-2]
 ```
  👉 작은 부분 문제에서 구한 최적의 답으로 합쳐진 큰 문제의 최적의 답을 구할 수 있어야 한다는 것

## 구현 방식
1. 큰 문제를 작은 문제로 나눌 수 있어야 함
2. 작은 문제들이 반복해 나타나고 사용되며 이 작은 문제들의 결과 값은 항상 같아야 함
3. 모든 작은 문제들은 한 번만 계산해 DP 테이블에 저장, 추후 재사용할 땐 이 DP 테이블 이용
4. 동적 계획 법을 톱 다운 방식과 바텀 업 방식으로 구현

## Bottom-Up vs Top-Down

### Bottom-Up 방식
- 가장 작은 부분 문제부터 큰 문제로 해결하는 방식
- 반복을 통해 DP[0] 부터 하나 씩 채우는 과정을 table-filling 이라 함
- 이 Table에 직접 접근하여 재활용하므로 Tabulation이라는 명칭이 붙었다고 함 (Memoization 기법과 크게 다르지 않음)
- for문을 이용해 해결하는 방식

```java
private static long Fibonacci(int n) {
		// 기저 조건을 기반으로 테이블을 채워나간다(Tabulation).
		for(int i = 3; i <= n; i++) {
			// 점화식을 이용하여 쉽게 구할 수 있다.
			dp[i] = dp[i - 1] + dp[i - 2];
		}
		
		return dp[n];
	}
```

### Top-Down 방식
- 위에서 부터 문제를 파악해 내려오는 방식
- 결과 값을 재귀를 통해 전이시켜 재활용하는 방식
- 피보나치 예시처럼 f(n) = f(n-2) + f(n+1) 의 과정에서 함수 호출 트리의 과정에서 보이 듯, n=5 일 때, f(3), f(2)의 동일한 계산이 반복적으로 나옴
- 이미 이전의 문제 해결 값을 저장해두었다가 꺼내서 활용한다고 하여 Memoziation 이라고 부름

```java
private static long Fibonacci(int n) {
		// 기저 조건(피보나치 수열의 초항).
		if (n == 1 || n == 2) {
			return dp[n] = 1;
		}
		// 만일, 저장된 값이 존재하는 경우 기억된 값을 바로 넘겨준다.
		if (dp[n] != 0) {
			return dp[n];
		}
		// 그렇지 않은 경우, 기저 조건까지 내려가서 구해진 값을 저장하면서 재귀를 전이한다.
		else {
			return dp[n] = Fibonacci(n - 1) + Fibonacci(n - 2);
		}
	}
```

## 실습
https://velog.io/@dnu05043/%EB%B0%B1%EC%A4%80-Fibonacci-2747%EB%B2%88-%EB%AC%B8%EC%A0%9C

## 추천 실습 문제
https://www.acmicpc.net/problem/11726

## 참고
https://sskl660.tistory.com/87
https://www.inflearn.com/course/%EB%91%90%EC%9E%87-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%9E%90%EB%B0%94/dashboard
