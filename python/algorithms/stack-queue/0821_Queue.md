## BFS

### 그래프를 탐색하는 방법

![0821_Queue_2025-08-21-08-45-34](images/0821_Queue_2025-08-21-08-45-34.png)

### 너비우선탐색(BFS, Breadth First Search)의 개념
탐색 시작점의 인접한 정점들을 모두 차례로 방문한 후에, 방문했던 정점을 시작점으로 하여 다시 인접한 정점들을 차례로 방문하는 방식

- 인접한 정점들에 대해 탐색을 한 후, 차례로 다시 너비우선탐색을 진행해야 하므로, 선입선출 형태의 자료구조인 큐룰 활용

### BFS의 탐색 순서

![0821_Queue_2025-08-21-08-47-05](images/0821_Queue_2025-08-21-08-47-05.png)

### BFS 알고리즘
- 입력 파라미터: 그래프 G와 탐색 시작점 v

```py
def bfs(G, v):  # 그래프 G, 탐색 시작점 v
    visited = [0] * (n + 1)             # n: 정점의 개수
    queue = []                          # 큐 생성
    queue.append(v)                     # 시작점 v를 큐에 삽입
    while queue:                        # 큐가 비어있지 않은 경우
        t = queue.pop(0)                # 큐의 첫 번째 원소 반환
        if not visited[t]:              # 방문되지 않은 곳이라면
            visited[t] = True           # 방문한 것으로 표시
            visit(t)                    # 정점 t에서 할 일
            for i in G[t]:              # t와 연결된 모든 정점에 대해
                if not visited[i]:      # 방문되지 않은 곳이라면
                    queue.append(i)     # 큐에 넣기
```

### BFS 예제 1
- 초기 상태
    - visited 배열 초기화
    - Q 생성
    - 시작점 enqueue

![0821_Queue_2025-08-21-09-10-27](images/0821_Queue_2025-08-21-09-10-27.png)

- A점부터 시작
    - dequeue: A
    - A 방문한 것으로 표시
    - A의 인접점 enqueue

![0821_Queue_2025-08-21-09-11-37](images/0821_Queue_2025-08-21-09-11-37.png)

- 탐색 진행
    - dequeue: B
    - B 방문한 것으로 표시
    - B의 인접점 enqueue

![0821_Queue_2025-08-21-09-12-33](images/0821_Queue_2025-08-21-09-12-33.png)

- 탐색 진행
    - dequeue: C
    - C 방문한 것으로 표시
    - C의 인접점 enqueue

![0821_Queue_2025-08-21-09-19-49](images/0821_Queue_2025-08-21-09-19-49.png)

- 탐색 진행
    - dequeue: D
    - D 방문한 것으로 표시
    - D의 인접점 enqueue

![0821_Queue_2025-08-21-09-20-39](images/0821_Queue_2025-08-21-09-20-39.png)

- 탐색 진행
    - dequeue: E
    - E 방문한 것으로 표시
    - E의 인접점 enqueue

![0821_Queue_2025-08-21-09-22-31](images/0821_Queue_2025-08-21-09-22-31.png)

- 탐색 진행
    - dequeue: F
    - F 방문한 것으로 표시
    - F의 인접점 enqueue

![0821_Queue_2025-08-21-09-22-56](images/0821_Queue_2025-08-21-09-22-56.png)

- 탐색 진행
    - dequeue: G
    - G 방문한 것으로 표시
    - G의 인접점 enqueue

![0821_Queue_2025-08-21-09-23-37](images/0821_Queue_2025-08-21-09-23-37.png)

- 탐색 진행
    - dequeue: H
    - H 방문한 것으로 표시
    - H의 인접점 enqueue

![0821_Queue_2025-08-21-09-24-10](images/0821_Queue_2025-08-21-09-24-10.png)

- 탐색 진행
    - dequeue: I
    - I 방문한 것으로 표시
    - I의 인접점 enqueue

![0821_Queue_2025-08-21-09-24-36](images/0821_Queue_2025-08-21-09-24-36.png)

- Q가 비었으므로 탐색 종료

### BFS 예제 2
- 초기 상태
    - visited 배열 초기화
    - Q 생성
    - 시작점 enqueue

![0821_Queue_2025-08-21-09-25-30](images/0821_Queue_2025-08-21-09-25-30.png)

- 입력 파라미터: 그래프 G와 탐색 시작점 v와 정점의 개수 n

```py
def bfs(G, v):  # 그래프 G, 탐색 시작점 v
    visited = [0] * (n + 1)             # n: 정점의 개수
    queue = []                          # 큐 생성
    queue.append(v)                     # 시작점 v를 큐에 삽입
    while queue:                        # 큐가 비어있지 않은 경우
        t = queue.pop(0)                # 큐의 첫 번째 원소 반환
        if not visited[t]:              # 방문되지 않은 곳이라면
            visited[t] = True           # 방문한 것으로 표시
            visit(t)                    # 정점 t에서 할 일
            for i in G[t]:              # t와 연결된 모든 정점에 대해
                if not visited[i]:      # 방문되지 않은 곳이라면
                    queue.append(i)     # 큐에 넣기
                    # n으로부터 1만큼 이동
                    visited[i] = visited[t] + 1     
```

### BFS 예제 3

![0821_Queue_2025-08-21-09-28-37](images/0821_Queue_2025-08-21-09-28-37.png)

```py
"""
1 7
1 2 1 3 2 4 2 5 4 6 5 6 6 7 3 7
"""
# s: 탐색 시작하는 정점
def bfs(s):
    # 방문 배열: 중복방문 체크 + 거리 계산
    visited = [0] * (V + 1)

    # 큐
    q = deque()

    # 시작 정점 큐에 추가
    q.append(s)

    # 방문 체크
    visited[s] = 1

    # 큐 안에 방문할 곳이 남아있으면 탐색
    while q:
        # 방문할 곳 꺼내기
        v = q.popleft()

        print(v, end=" ")

        # v와 인접한 정점을 탐색, 갈 수 있으면 큐에 저장
        # 1) 인접 행렬: v에서 nv로 갈 수 있는지 알 수 있음
        for nv in range(1, V+1):
            # 1. v에서 nv 정점으로 갈 수 있음
            # 2. nv를 방문한적이 없다.
            if adj_m[v][nv] == 1 and not visited[nv]:
                # nv 방문 예정인 사실을 저장
                q.append(nv)
                # nv까지 거리 = v까지 거리 + 1
                visited[nv] = visited[v] + 1

        # 2) 인접 리스트: v에서 갈 수 있는 정점만 들어있음
        for nv in adj_l:
            # 1. nv를 방문한적이 없다.
            if not visited[nv]:
                # nv 방문 예정인 사실을 저장
                q.append(nv)
                # nv까지 거리 = v까지 거리 + 1
                visited[nv] = visited[v] + 1

# 정점 갯수: V, 간선 갯수: E
V, E = map(int, input().split())
# 인접 행렬
adj_m = [[0] * (V + 1) for _ in range(V + 1)]
# 인접 리스트
adj_l = [[] for _ in range(V + 1)]
# 그래프 정보가 한 줄일 때
graph = list(map(int, input().split()))

for i in graph:
    s, e = graph[i * 2], graph[i * 2 + 1]

    # 인접 행렬
    adj_m[s][e] = 1
    adj_m[e][s] = 1
    
    # 인접 리스트
    adj_l[s].append(e)
    adj_l[e].append(s)
```

### 실습
- 큐
    - 5907. 회전
- 시뮬레이션
    - 5099. 피자 굽기
- BFS
    - 5102. 노드의 거리
    - 5106. 미로의 거리
- 추가 연습
    - 10966. 물놀이를 가자
