# DP(Dynamic Programming)
## 문제 유형

1. 최적 부분 구조 : 큰 문제를 작은 문제로 나눌 수 있음
2. 중복되는 부분 문제 : 동일한 작은 문제를 반복적으로 해결
- Top-down 방식 (재귀함수)
    - 메모이제이션 - 한번 계산할 결과를 DP 테이블에 저장해두었다가 같은 문제가 호출되면 메모했던 결과를 불러옴
- Bottom-up (반복문)s



## 피보나치 수

```python
dp = [0] * 100

# Top-down
def fibo(x):
	if x == 1 or x == 2:
		return 1
	if dp[x] != 0:
		return dp[x]
	dp[x] = fibo(x-1) + fibo(x-2)
	return dp[x]

print(fibo(99))

# Bottom-up
dp = [0] * 100
dp[1] = 1
dp[2] = 1
n = 99
for i in range(2, n+1):
	dp[i] = dp[i-1] + dp[i-2]
print(dp[n])

```

## 1로 만들기
![image](https://user-images.githubusercontent.com/49435163/149655979-f16f3e4d-e9fc-4b73-a78f-a242c268be5b.png)

$$
a_{i} = min(a_{i-1} , a_{i/2}, a_{i/3}) + 1
$$


```python
#if-elif로 하면 2,3으로 둘다 나누어지는 경우 잡지 못하므로, if문으로
N = int(input())
dp = [0] * (N+1)
for i in range(2, N+1):
		# 현재의 수에서 1 빼는 경우
    dp[i] = dp[i - 1] + 1
    #현재의 수가 2로 나누어 떨어지는 경우
		if i % 2 == 0:
        dp[i] = min(dp[i//2]+1, dp[i])
    #현재의 수가 3으로 나누어 떨어지는 경우
		if i % 3 == 0:
        dp[i] = min(dp[i//3]+1, dp[i])

print(dp[N])
# N = 10
# dp = [0, 0, 1, 1, 2, 3, 2, 3, 3, 2, 3]
```

## 구간합

$$
a_{i}(i 까지의 합) = x_{i}(현재 값) + a_{i-1}(i-1까지의 합)
$$

```python
import sys
input = sys.stdin.readline
N, M = map(int, input().split())
num_list = list(map(int, input().split()))
dp = [0] * (N+1)
# dp[i] = i 까지의 합
for idx, num in enumerate(num_list):
    dp[idx+1] = dp[idx] + num
# s~f 까지의합 = dp[f] - dp[s-1]
for _ in range(M):
    s, f = map(int, input().split())
    print(dp[f]-dp[s-1])
```

## 가장 긴 증가/감소하는 부분수열

```python
N = int(input())
dp = [0] * (N + 1)
if N >= 2:
    dp[2] = 1

# Bottom-Up
for i in range(3, N + 1):
dp[i] = min(dp[i // 2] + (i % 2), dp[i // 3] + (i % 3)) + 1

# Top-down
def td(n):
    if n <= 2:
        return dp[n]
    dp[n] = min(td(n // 3) + (n % 3), td(n // 2) + (n % 2)) + 1
    return dp[n]
td(N)

print(dp[N])
```
## 배낭 문제


## LCS
