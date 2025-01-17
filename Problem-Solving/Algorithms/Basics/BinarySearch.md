# 이진 탐색 (Binary Search) 개념 정리

이진 탐색은 정렬된 배열에서 원하는 값을 효율적으로 찾는 알고리즘입니다.  
탐색 범위를 절반으로 나누며 값을 찾기 때문에, 시간 복잡도가 매우 낮습니다.

---

## 1. 이진 탐색의 특징

1. **전제 조건**: 데이터가 반드시 정렬된 상태여야 합니다.
2. **탐색 방식**: 중간값을 기준으로 탐색 범위를 반으로 줄여가며 값을 찾습니다.
3. **시간 복잡도**: O(log n)  
   - n은 데이터의 크기.

---

## 2-1. 기본 원리

1. **초기 범위 설정**: 배열의 **왼쪽 끝**을 `l`, **오른쪽 끝**을 `r`로 설정합니다.
2. **중앙값 계산**: `mid = (l + r) // 2`로 중앙값을 계산합니다.
3. **비교**:
    - `arr[mid]`와 찾고자 하는 값(`target`)을 비교합니다.
    - 값이 **작으면 왼쪽**, **크면 오른쪽**으로 범위를 좁혀갑니다.
    - 찾으면 값을 반환하고 종료합니다.

## 2-2. 범위 조정

- **왼쪽 탐색 (더 작은 값)**:
    - r = mid - 1
    - `mid` 값이 조건을 만족하지 않으면, 탐색 범위를 왼쪽 절반으로 좁히기 위해 `r`을 `mid - 1`로 설정합니다.

- **오른쪽 탐색 (더 큰 값)**:
    - l = mid + 1
    - `mid` 값이 조건을 만족하지 않으면, 탐색 범위를 오른쪽 절반으로 좁히기 위해 `l`을 `mid + 1`로 설정합니다.

---

## 3. 이진 탐색의 구현

### 1) 반복문을 사용한 구현 (Python)
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1

    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid  # 값 찾음
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1  # 값 없음

# 테스트
array = [1, 3, 5, 7, 9, 11]
target = 7
print(binary_search(array, target))  # 출력: 3 (인덱스)
```

### 2) 재귀를 사용한 구현 (Python)
```python
def binary_search_recursive(arr, target, left, right):
    if left > right:
        return -1  # 값 없음

    mid = (left + right) // 2

    if arr[mid] == target:
        return mid  # 값 찾음
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, right)
    else:
        return binary_search_recursive(arr, target, left, mid - 1)

# 테스트
array = [1, 3, 5, 7, 9, 11]
target = 7
print(binary_search_recursive(array, target, 0, len(array) - 1))  # 출력: 3
```

---

## 4. 이진 탐색의 시간 복잡도

- **시간 복잡도**: O(log n)  
  - 한 번의 비교로 탐색 범위를 절반으로 줄이기 때문.
- **공간 복잡도**:  
  - 반복문: O(1) (추가 메모리 필요 없음).  
  - 재귀: O(log n) (재귀 호출에 따른 호출 스택 메모리 사용).

---

## 5. 이진 탐색의 활용 사례

1. **정렬된 배열에서 값 찾기**
   - 데이터베이스, 검색 엔진 등.
2. **Lower Bound / Upper Bound**
   - 특정 값 이상의 첫 위치나 특정 값 초과의 첫 위치 찾기.
3. **매개변수 탐색**
   - 최적화 문제에서 답을 결정하는 매개변수 값 찾기.
4. **정렬된 데이터에서 삽입 위치 찾기**
   - 새로운 데이터를 삽입할 때 효율적으로 위치를 결정.

---

## 실습 문제

### 1. 기본 문제
1. [백준 1920번: 수 찾기](https://www.acmicpc.net/problem/1920)  
2. [백준 10816번: 숫자 카드 2](https://www.acmicpc.net/problem/10816)  
3. [백준 2512번: 예산](https://www.acmicpc.net/problem/2512)

### 2. 응용 문제
4. [백준 2805번: 나무 자르기](https://www.acmicpc.net/problem/2805)
5. [백준 2110번: 공유기 설치](https://www.acmicpc.net/problem/2110)  
6. [백준 12015번: 가장 긴 증가하는 부분 수열 2](https://www.acmicpc.net/problem/12015)

### 3. 실전 문제
7. [백준 2470번: 두 용액](https://www.acmicpc.net/problem/2470)  
8. [프로그래머스: 거리두기 확인하기](https://school.programmers.co.kr/learn/courses/30/lessons/81302)  
9. [프로그래머스: 입국심사](https://school.programmers.co.kr/learn/courses/30/lessons/43238)  
10. [프로그래머스: 징검다리](https://school.programmers.co.kr/learn/courses/30/lessons/43236)  