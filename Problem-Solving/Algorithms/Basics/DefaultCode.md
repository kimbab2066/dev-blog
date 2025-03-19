# 기본 틀 정리

## 1. 중복 없이 r개를 뽑는 조합 (itertools.combinations와 동일한 결과)
```python
def dfs(idx, path, n, r):
    if len(path) == r:
        print(path)
        return

    for i in range(idx, n):
        dfs(i + 1, path + [arr[i]], n, r)

arr = [10, 20, 30, 40]
r = 2  # 2개를 뽑는 조합
dfs(0, [], len(arr), r)
```
## 2. 중복을 허용하는 조합 (itertools.combinations_with_replacement와 동일한 결과)
```python
def dfs(idx, path, n, r):
    if len(path) == r:
        print(path)
        return

    for i in range(idx, n):
        dfs(i, path + [arr[i]], n, r)  # i+1 대신 i를 넘겨줌 (중복 허용)

arr = [10, 20, 30, 40]
r = 2  # 2개를 뽑는 중복 조합
dfs(0, [], len(arr), r)
```

## 프림(Prim)
```python
import heapq

def prim(N, graph):
    visited = [False] * (N + 1)  # 방문 체크
    pq = [(0, 1)]  # (비용, 노드) 형식으로 최소 힙 사용
    total_weight = 0

    while pq:
        weight, node = heapq.heappop(pq)
        
        if visited[node]:  # 이미 방문한 노드는 무시
            continue

        visited[node] = True
        total_weight += weight

        for next_node, next_weight in graph[node]:
            if not visited[next_node]:  # 방문하지 않은 노드만 추가
                heapq.heappush(pq, (next_weight, next_node))

    return total_weight

# 그래프 입력 예시
N = 5  # 노드 개수
edges = [
    (1, 2, 3), (1, 3, 1), (2, 3, 1), (2, 4, 6), (3, 4, 5), (3, 5, 4), (4, 5, 2)
]

# 인접 리스트로 변환
graph = {i: [] for i in range(1, N+1)}
for u, v, w in edges:
    graph[u].append((v, w))
    graph[v].append((u, w))  # 무방향 그래프

# 실행
print(prim(N, graph))  # 최소 스패닝 트리의 가중치 합 출력
```