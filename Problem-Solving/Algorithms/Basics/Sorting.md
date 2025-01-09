# Sorting Algorithms (정렬 알고리즘)

정렬 알고리즘은 데이터를 특정 순서대로 정렬하는 데 사용됩니다.  
가장 기초적인 알고리즘으로 코딩 테스트와 실무에서 필수적으로 사용됩니다.

---

## 주요 정렬 알고리즘

### 1. **버블 정렬 (Bubble Sort)**  
- 인접한 두 요소를 비교하여 교환하며 정렬합니다.  
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

---

## 실습 문제

1. [백준 2750번: 수 정렬하기](https://www.acmicpc.net/problem/2750)  
2. [백준 10989번: 수 정렬하기 3](https://www.acmicpc.net/problem/10989)  
3. [백준 11650번: 좌표 정렬하기](https://www.acmicpc.net/problem/11650)  
4. [프로그래머스: K번째 수](https://school.programmers.co.kr/learn/courses/30/lessons/42748)  
5. [프로그래머스: 가장 큰 수](https://school.programmers.co.kr/learn/courses/30/lessons/42746)  
6. [프로그래머스: H-Index](https://school.programmers.co.kr/learn/courses/30/lessons/42747)  
7. [프로그래머스: 실패율](https://school.programmers.co.kr/learn/courses/30/lessons/42889)  
8. [프로그래머스: 정렬된 배열에서 특정 수의 개수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/43237)  
9. [프로그래머스: 이중우선순위큐](https://school.programmers.co.kr/learn/courses/30/lessons/42628)  
10. [프로그래머스: 카펫](https://school.programmers.co.kr/learn/courses/30/lessons/42842)
