### 조합

```python
def f(i, V): # V개의 집합에서 i 원소의 포함여부 결정
    if i == V: # 모든 원소에 대해 결정하면
        print(b)
    else:
        b[i] = 1        # a[i] 원소가 부분집합에 포함
        f(i + 1, V)     # 다음 원소를 찾으러 가봐
        b[i] = 0        # a[i] 원소가 부분집합에 포함되지 않음
        f(i + 1, V)
        
def f0(i, V): # V개의 집합에서 i 원소의 포함여부 결정
    if i == V: # 모든 원소에 대해 결정하면
        for i in range(V):
            if b[i]:
                print(arr[i], end=' ')
        print()
    else:
        b[i] = 1        # a[i] 원소가 부분집합에 포함
        f0(i + 1, V)     # 다음 원소를 찾으러 가봐
        b[i] = 0        # a[i] 원소가 부분집합에 포함되지 않음
        f0(i + 1, V)
        
'---------------------------------------------------------------------'

# 응용

def combi(i, N): # 조합으로 해보자
    global b
    global arr
    global score_list
    if i == N:
        if sum(b) == N//2: # 만약 b에서 True가 절반이라면
            type_A = []
            type_B = []
            for j in range(N):
                if b[j]: # 1이면 type_A에 담고
                    type_A.append(arr[j])
                else:   # 0이면 type_B에
                    type_B.append(arr[j])
            print(type_A, type_B)
            taste_score = abs(cal_taste(type_A) - cal_taste(type_B))
            score_list.append(taste_score)
    else:
        b[i] = 0
        combi(i + 1, N)
        b[i] = 1
        combi(i + 1, N)
```

### 순열

```python
def f(idx, N):
	if idx == N:
		print(arr)
	else:
		for i in range(idx, N):
			arr[idx], arr[i] = arr[i], arr[idx] # 순서를 바꾸고
			f(idx + 1, N)
			arr[idx], arr[i] = arr[i], arr[idx] # 원상 복구

arr = [1, 2, 3]
N = 3
f(0, N)

```

### DFS

```python
def DFS(s, V):                  # s 시작 정점 / V 정점 개수
    visited = [0] * (V + 1)     # 방문한 정점을 표시하기 위함
    stack = []                  # 스택 생성

    print(s, end=' ')
    visited[s] = 1  # 출발지(시작점)을 방문했다고 표시
    visit = s       # visit 현재 정점
    while 1:
        for w in adjL[visit]:       # v에 인접하고, 방문 안 한 w가 있으면
            if visited[w] == 0:
                stack.append(visit) # 현재 정점을 push하고
                visit = w           # w에 방문
                print(visit, end=' ')
                visited[w] = 1      # w에 방문 표시
                break               # for w: visit부터 다시 탐색
        else:                       # 남은 인접 정점이 없어서 break가 걸리지 않은 경우
            if stack:               # 이전 갈림길을 스택에서 꺼내서 (== if top > -1:)
                visit = stack.pop()
            else:                   # 되돌아갈 곳이 없고 남은 갈림길이 없으면 탐색 종료
                break               # while 1:
```

```python
# 미로

def dfs(s_i, s_j, N):
    stack = [] # 되돌아갈 때 사용할 스택
    visited[s_i][s_j] = 1 # 방문 표시
    n_i, n_j = s_i, s_j # 현재위치 표시
 
    di = [1, 0, -1, 0]
    dj = [0, 1, 0, -1]
 
    while 1:
        if maze[n_i][n_j] == 3: # 도착하면
            return 1
        for k in range(4):
            mi, mj = n_i + di[k], n_j + dj[k]
            # 범위를 벗어나지 않고, 해당 위치가 벽이 아니며, 방문하지 않아다면
            if 0 <= mi < N and 0 <= mj < N and maze[mi][mj] != 1 and visited[mi][mj] == 0:
                stack.append([n_i, n_j])    # 스택에 현 위치 삽입
                n_i, n_j = mi, mj           # 이동
                visited[n_i][n_j] = 1       # 방문 표시
                break
        else: # for문을 다 돌았는데 (4방향을 다 봤는데, 없어서 정상 종료 됐따면)
            if stack: # 스택에 자료가 있으면
                n_i, n_j = stack.pop()
            else:  # 없으면
                return 0 # 0 반환
    return -1 # 비정상 종료
    # 마지막 리턴 위치 잘 보자. 왜 안 되나 했네.... ㅜ
 
```

### BFS

```python
def BFS(s, V): # 시작점, 정점 수
    visited = [0] * (V + 1) # visited 생성
    queue = []              # 큐 생성
    queue.append(s)         # 시작점 enqueue
    visited[s] = 1          # 시작점 방문 표시
    while queue:            # queue에 자료가 있는 동안 (탐색할 정점이 남아있으면)
        t = queue.pop(0)    # t를 dequeue
        print(t, end=' ')   # visit(t) # 할 작업
        for w in adjL[t]:   # 뽑은 t에 연결된 곳이 있는지 확인
            if visited[w] == 0: # 만약 뽑은 것이 방문된 적이 없는 곳이라면 (queue에 들어간 적이 없다면)
                queue.append(w) # queue에 enQueue
                visited[w] = 1  # enQueue 된 적이 있음을 표시
    print()
```

```python
# 미로

from collections import deque

def find_start(N, maze):
    for i in range(N):
        for j in range(N):
            if maze[i][j] == 2:
                return i, j

def BFS(si, sj, N):
    visited = [[0] * N for _ in range(N)]
    q = deque()
    q.append((si, sj))
    visited[si][sj] = 1

    di = [1, 0, -1, 0]
    dj = [0, 1, 0, -1]

    while q:
        i, j = q.popleft()
        if maze[i][j] == 3:
            print(visited)
            print(q)
            return visited[i][j] - 1 - 1 # 경로의 빈 칸 수
        for k in range(4):
            mi, mj = i + di[k], j + dj[k]
            if 0 <= mi < N and 0 <= mj < N and maze[mi][mj] != 1 and visited[mi][mj] == 0:
                q.append((mi, mj))
                visited[mi][mj] = visited[i][j] + 1
    return 0 # 도달 못하는 경우
```

### 소수 구하기

```python
def prime(x):
    if x == 0 or x == 1:
        return False
    for i in range(2, int(j ** 0.5) + 1):
        if x % i == 0:
            return False
    return True

n, m = map(int, input().split())

for j in range(n, m + 1):
    if prime(j):
        print(j)
```