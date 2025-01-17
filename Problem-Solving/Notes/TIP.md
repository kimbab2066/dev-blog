# Rotate 관련 정리

---

## 📌 Rotate란?
- 특정 자료구조에서 데이터를 **좌/우로 회전**시키는 연산.
- 자료구조에 따라 구현 방식이 달라짐.
- 효율적인 회전을 위해 특정 자료구조(`deque` 등)를 활용하거나 직접 구현 가능.

---

## 🔧 Rotate가 가능한 자료구조와 구현

### 1. **리스트 (List)**
리스트의 원소를 슬라이싱을 통해 회전.

#### 🔹 코드 예시:
```python
arr = [1, 2, 3, 4, 5]
k = 2  # 오른쪽으로 2번 회전

# 오른쪽 회전
rotated = arr[-k:] + arr[:-k]
print(rotated)  # [4, 5, 1, 2, 3]

# 왼쪽 회전
rotated = arr[k:] + arr[:k]
print(rotated)  # [3, 4, 5, 1, 2]
```

---

### 2. **Deque (양방향 큐)**
`collections.deque`의 `rotate` 메서드를 사용해 효율적으로 회전.

#### 🔹 코드 예시:
```python
from collections import deque

dq = deque([1, 2, 3, 4, 5])
dq.rotate(2)  # 오른쪽으로 2번 회전
print(dq)  # deque([4, 5, 1, 2, 3])

dq.rotate(-2)  # 왼쪽으로 2번 회전
print(dq)  # deque([1, 2, 3, 4, 5])
```

---

### 3. **문자열 (String)**
문자열은 불변 자료구조이므로 슬라이싱으로 새로운 문자열 생성.

#### 🔹 코드 예시:
```python
s = "abcdef"
k = 2

# 오른쪽 회전
rotated = s[-k:] + s[:-k]
print(rotated)  # "efabcd"

# 왼쪽 회전
rotated = s[k:] + s[:k]
print(rotated)  # "cdefab"
```

---

### 4. **배열 (Array)**
`numpy` 라이브러리의 `roll` 메서드를 활용.

#### 🔹 코드 예시:
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
rotated = np.roll(arr, 2)  # 오른쪽으로 2번 회전
print(rotated)  # [4 5 1 2 3]
```

---

### 5. **링크드 리스트 (Linked List)**
링크드 리스트는 노드를 끊고 재배치하는 방식으로 회전 구현.
복잡한 구현이 필요하며, 시간 복잡도는 O(n).

---

### 6. **트리 (Tree)**
트리에서는 회전 연산을 통해 트리의 균형을 유지.
AVL 트리, 레드-블랙 트리 등에서 사용.

#### 🔹 트리 회전 예시:
- 왼쪽 회전: 오른쪽 자식이 새로운 루트.
- 오른쪽 회전: 왼쪽 자식이 새로운 루트.

---

## 📎 추가 팁
- 리스트와 문자열은 슬라이싱으로 간단히 구현 가능.
- 효율성을 중시할 경우, `deque`의 `rotate` 메서드 사용.
- 데이터 크기가 클 경우, 시간 복잡도를 고려한 자료구조 선택 필요.
