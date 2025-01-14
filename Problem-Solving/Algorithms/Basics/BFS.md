# BFS (Breadth-First Search) 개념 정리

BFS는 그래프나 트리에서 너비 우선으로 탐색하는 알고리즘입니다.  
즉, 시작 정점에서 가까운 정점부터 먼저 탐색하고, 그다음으로 먼 정점을 탐색합니다.

---

## 1. BFS의 특징

1. **탐색 순서**: 루트 또는 시작 노드에서 출발하여 **가까운 노드**를 먼저 탐색.
2. **데이터 구조**: BFS는 **큐(Queue)** 자료구조를 사용.
3. **동작 방식**: 방문할 노드를 큐에 저장하고, 큐에서 노드를 하나씩 꺼내며 탐색.

---

## 2. BFS의 동작 과정

1. 시작 노드를 방문하고 큐에 삽입.
2. 큐에서 노드를 꺼내 연결된 모든 미방문 노드를 큐에 삽입.
3. 방문한 노드는 다시 방문하지 않도록 체크.
4. 큐가 빌 때까지 2~3 과정을 반복.

---

## 3. BFS의 구현

### 예제: 인접 리스트를 사용한 BFS 구현 (Python)

```python
from collections import deque

def bfs(graph, start):
    visited = []         # 방문한 노드 기록
    queue = deque([start])  # 큐 초기화

    while queue:
        node = queue.popleft()  # 큐에서 노드 꺼내기
        if node not in visited:
            visited.append(node)  # 방문 처리
            queue.extend(graph[node])  # 연결된 노드 추가

    return visited

# 예제 그래프 (인접 리스트)
graph = {
    1: [2, 3, 4],
    2: [5, 6],
    3: [],
    4: [7],
    5: [],
    6: [],
    7: []
}

# BFS 실행
print(bfs(graph, 1))  # 출력: [1, 2, 3, 4, 5, 6, 7]
```

---

## 4. BFS의 시간 복잡도

- **시간 복잡도**: O(V + E)  
  - V: 노드(정점)의 수  
  - E: 간선의 수
- **공간 복잡도**: O(V)  
  - 큐와 방문 체크를 위한 공간 필요

---

## 5. BFS의 활용 사례

1. **최단 경로 탐색**
   - 무방향 그래프에서 가중치가 동일한 간선일 경우, BFS는 최단 경로를 보장합니다.
2. **그래프 연결 요소 확인**
   - 그래프가 몇 개의 연결 요소로 이루어져 있는지 확인.
3. **Flood Fill 알고리즘**
   - 그림이나 격자 형태의 영역을 채우는 데 사용.
4. **웹 크롤러**
   - 링크를 따라 순차적으로 페이지를 탐색.

---

## 6. BFS와 DFS 비교

| 특성        | BFS (너비 우선 탐색)    | DFS (깊이 우선 탐색)    |
|-------------|-------------------------|-------------------------|
| 탐색 방식   | 가까운 노드부터 탐색     | 깊은 노드부터 탐색       |
| 사용 구조   | 큐 (Queue)              | 스택 (Stack) 또는 재귀    |
| 최단 경로 보장 | 가능                    | 보장하지 않음            |

---

## 실습 문제

1. [백준 1260번: DFS와 BFS](https://www.acmicpc.net/problem/1260)  
2. [백준 2178번: 미로 탐색](https://www.acmicpc.net/problem/2178)  
3. [백준 2606번: 바이러스](https://www.acmicpc.net/problem/2606)  
4. [프로그래머스: 게임 맵 최단거리](https://school.programmers.co.kr/learn/courses/30/lessons/1844)  
5. [프로그래머스: 아이템 줍기](https://school.programmers.co.kr/learn/courses/30/lessons/87694)  
6. [프로그래머스: 블록 이동하기](https://school.programmers.co.kr/learn/courses/30/lessons/60063)  
7. [백준 1707번: 이분 그래프](https://www.acmicpc.net/problem/1707)  
8. [백준 7576번: 토마토](https://www.acmicpc.net/problem/7576)  
9. [프로그래머스: 네트워크](https://school.programmers.co.kr/learn/courses/30/lessons/43162)  
10. [백준 1012번: 유기농 배추](https://www.acmicpc.net/problem/1012)
