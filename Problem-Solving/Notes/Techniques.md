## **Python 최적화 기법 정리**

### **1. 리스트 컴프리헨션 (List Comprehension)**
- 리스트를 간결하게 생성하는 방법
```python
arr = [i**2 for i in range(10)]
```

### **2. 람다 함수 (Lambda Function)**
- 익명 함수를 간단하게 정의하는 방법
```python
add = lambda x, y: x + y
print(add(2, 3))  # 5
```

### **3. ZIP과 ENUMERATE 활용**
- `zip()`을 사용해 두 리스트를 묶어 처리
```python
a = [1, 2, 3]
b = ['x', 'y', 'z']
print(list(zip(a, b)))  # [(1, 'x'), (2, 'y'), (3, 'z')]
```
- `enumerate()`로 인덱스와 값을 동시에 활용
```python
arr = ['a', 'b', 'c']
for i, val in enumerate(arr):
    print(i, val)
```

### **4. 해시 (딕셔너리 활용)**
- `set`을 이용한 빠른 탐색 (`O(1)`)
```python
s = set([1, 2, 3])
print(2 in s)  # True
```

### **5. 기본 라이브러리 활용**
- **Counter (빈도수 세기)**
```python
from collections import Counter
c = Counter("hello")
print(c)  # {'h': 1, 'e': 1, 'l': 2, 'o': 1}
```
- **defaultdict (기본값 설정)**
```python
from collections import defaultdict
d = defaultdict(int)
d['a'] += 1
print(d)  # {'a': 1}
```

### **6. 우선순위 큐 (힙) 활용**
- **최소/최대 힙을 활용한 정렬 및 우선순위 처리**
```python
import heapq
q = [3, 1, 4, 1, 5]
heapq.heapify(q)  # 최소 힙 변환
print(heapq.heappop(q))  # 1 (최소값)
```

### **7. 비트 마스킹**
- **이진수를 활용해 부분 집합을 빠르게 계산**
```python
for i in range(1 << 3):  # 2^3 개의 부분집합 생성
    subset = [j for j in range(3) if i & (1 << j)]
    print(subset)
```

### **8. 최적화 팁**
1. **리스트 vs 딕셔너리**
   - 리스트 탐색: `O(N)`
   - 딕셔너리 조회: `O(1)`
2. **`if-else` 대신 `dict` 활용**
   ```python
   func_dict = {'A': func1, 'B': func2}
   result = func_dict.get(key, default_func)()
   ```
3. **반복문 대신 map/filter 사용**
   ```python
   numbers = [1, 2, 3, 4]
   squares = list(map(lambda x: x**2, numbers))
   evens = list(filter(lambda x: x % 2 == 0, numbers))
   ```

### **9. 문자열 변환**

   ```python
   x = chr(97 + (ord(x) - 97 + 1)%26)
   ```
   
### **10. 배열 회전**
    회전 방향	좌표 변환 방식
    시계 방향 90도	(i, j) → (j, m - 1 - i)
    반시계 방향 90도	(i, j) → (m - 1 - j, i)
    180도 회전	(i, j) → (m - 1 - i, m - 1 - j)