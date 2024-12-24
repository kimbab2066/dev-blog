# Sorting Algorithms (정렬 알고리즘)

정렬 알고리즘은 데이터를 특정 순서대로 정렬하는 데 사용됩니다.  
가장 기초적인 알고리즘으로 코딩 테스트와 실무에서 필수적으로 사용됩니다.

---

## 주요 정렬 알고리즘

### 1. **버블 정렬 (Bubble Sort)**  
- 설명: 인접한 두 요소를 비교하여 교환하며 정렬합니다.  
- 시간 복잡도: O(n²)

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr

print(bubble_sort([5, 2, 9, 1, 5, 6]))
```

### 2. **퀵 정렬 (Quick Sort)**
   - 분할 정복(Divide and Conquer) 알고리즘으로 효율적입니다.
   - 시간 복잡도: O(n log n) (평균)
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

print(quick_sort([5, 2, 9, 1, 5, 6]))
```
### 3. **병합 정렬 (Merge Sort)**
   - 분할 정복 기법으로 안정적인 정렬 방식.
   - 시간 복잡도: O(n log n)
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])
    result.extend(right[j:])
    return result

print(merge_sort([5, 2, 9, 1, 5, 6]))
```
## 실습 문제

1. [백준 2750번: 수 정렬하기](https://www.acmicpc.net/problem/2750)  
   <details>
   <summary>문제 설명</summary>
   난이도: 브론즈 I  
   N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하세요.
   </details>

2. [프로그래머스: K번째 수](https://school.programmers.co.kr/learn/courses/30/lessons/42748)  
   <details>
   <summary>문제 설명</summary>
   난이도: Level 1  
   배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하세요.
   </details>
