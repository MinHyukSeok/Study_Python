# DP
- 동적 계획 알고리즘은 그리디 알고리즘과 같이 최적화 문재를 해결하는 알고리즘이다.
- 동적 계획 알고리즘은 먼저 입력 크기가 작은 부분 문제들을 모두 해결한 후애 그 해들을 이용하여 보다 큰 크기의 부분 문제들을 해결하여, 최종적으로 원래 주어진 입력의 문제를 해결하는 알고리즘
  
``` python
# 피보나치 수 DP 적용 알고리즘

def fibo(n):
    f = [0] * (n + 1)

    f[0] = 0
    f[1] = 1

    for i in range(2, n + 1):
        f[i] = f[i - 1] + f[i - 2]

    return f[n]


```

## DFS(깊이 우선 탐색)

- 비선형구조인 그래프 구조는 그래프로 표현된 모든 자료를 빠짐없이 검색하는 것이 중요함
- 두 가지 방법
  - 깊이 우선 탐색
  - 너비 우선 탐색

1. 시작 정점 v를 결정하여 반문한다.
2. 정점 v에 인접한 정점 중에서
   1. 방문하지 않은 정점 w가 있으면, 정점 v를 스텍에 push하고 정점 w를 반문한다.
   2. 방문하지 않은 정점이 없다면, 탐색의 방향을 바꾸기 위해서 스택을 pop하여 받은 가장 마지막 방문 정접을 v로하여 다시 2. 반복
3. 스택이 공백이 될 때까지 2. 반복

```python

# 7 8
# 1 2 1 3 2 4 2 5 4 6 5 6 6 7 3 7

V, E = map(int, input().split())
arr = list(map(int, input().split()))
adJM = [[0] * (v + 1) for _ in range(V + 1)]

for i in range(E):
    v1, v2 = arr[i * 2], arr[i * 2 + 1]   # 두 개씩 읽어오기
    adJM[v1][v2] = 1
    adJM[v2][v1] = 1
```

```python
V, E = map(int, input().split())
arr = list(map(int, input().split()))
adJM = [[0] * (v + 1) for _ in range(V + 1)]
adjL = [[] for _ in range(V + 1)]
for _ in range(E):
    v1, v2 = arr[i * 2], arr[i * 2 + 1]   # 두 개씩 읽어오기
    adJM[v1][v2] = 1
    adJM[v2][v1] = 1

    adjL[v1].append(v2)
    adjL[v2].append(v1)


```

## 백트래킹
- 해를 찾는 도중에 막히면 되돌아가서 다시 해를 찾아 가는 기법
- 최적화 문제와 결정 문제를 해결할 수 있다.

``` python
def checknode(v):
    if promising(v:):
        if there is a solution at v:
            write the solution
        else:
            for u in each child of v:
                checknode(u)
```

### 부분집합 생성하기
```python 
bit = [0, 0, 0, 0]
for i in range(2):
    bit = i
    for j in range(2):
        bit[1] = j
        for k in range(2):
            bit[2] = k
            for l in range(2):
                bit[3] = l
                print(bit)

```
### {1,2,3}포함하는 모든 순열을 생성하는 함수
```python
for i1 in range(1, 4):
    for i2 in range(1, 4):
        if i2 != i1:
            for i3 in range(1, 4):
                if i3 != i1 and i3 != i2:
                    print(i1, i2, i3)

```

### {1,2,3,4,5,6,7,8,9,10}의 부분집합중 원소의 합이 10인 부분집합을 구하는 함수
```python
def backtrack(a, k, input):
    # a는 존재하는지 나타낸 리스트
    # k는 현재 위치
    # input은 끝나는 위치
    global MAXCANDIDATES
    c = [0] * MAXCANDIDATES

    if k == input:
        if sum(a) == 10:
            print(a)
    else:
        k += 1
        a[k] = k
        backtrack(a, k , input)
        a[k] = False
        backtrack(a, k ,input)

MAXCANDIDATES = 2
NMAX = 11
a = [0] * NMAX
backtrack(a, 0, 10)

```