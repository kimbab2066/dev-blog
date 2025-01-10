# 그리디 알고리즘(Greedy Algorithm) 개념 정리

그리디 알고리즘은 **현재 상황에서 가장 최선의 선택**을 반복하여 문제를 해결하는 알고리즘 설계 기법입니다.  
문제의 최적해를 보장하려면 각 단계에서의 선택이 전체적으로도 최적이라는 **최적 부분 구조**가 성립해야 합니다.

---

## 1. 그리디 알고리즘의 특징

1. **현재 선택의 최적성**
   - 매 단계에서 가장 최선의 선택을 합니다.
2. **최적 부분 구조**
   - 부분 문제의 최적해를 통해 전체 문제의 최적해를 구할 수 있어야 합니다.
3. **탐욕적 선택**
   - 이전 선택이 이후의 선택에 영향을 주지 않아야 합니다.

---

## 2. 그리디 알고리즘의 동작 과정

1. 문제를 부분 문제로 나눕니다.
2. 각 단계에서 최선의 선택을 합니다.
3. 모든 선택이 끝날 때까지 반복합니다.
4. 선택의 결과를 종합하여 최적해를 도출합니다.

### 예제: 동전 거스름돈 문제

- 입력: 거스름돈 금액과 동전 단위 (500원, 100원, 50원, 10원)
- 목표: 최소 동전 개수로 거스름돈을 지불하기

#### 알고리즘 동작
1. 가장 큰 단위의 동전부터 거슬러 줍니다.
2. 남은 금액에 대해 반복합니다.

---

## 3. 그리디 알고리즘의 활용

1. **최소 스패닝 트리(MST)**
   - 크루스칼 알고리즘, 프림 알고리즘.
2. **최단 경로 문제**
   - 다익스트라 알고리즘.
3. **스케줄링 문제**
   - 작업 우선순위 결정, 최소 회의실 배정.
4. **배낭 문제(단, 물건을 쪼갤 수 있는 경우)**
   - Fractional Knapsack Problem.
5. **기타 사례**
   - Huffman Coding, 동전 거스름돈 문제.

---

## 4. 그리디 알고리즘의 한계

1. **반례 가능성**
   - 모든 문제에서 항상 최적해를 보장하지는 않습니다.
   - 예: 배낭 문제에서 물건을 쪼갤 수 없는 경우(0-1 Knapsack Problem).
2. **최적 부분 구조**
   - 문제에 최적 부분 구조가 성립하지 않으면 그리디 접근이 실패할 수 있습니다.

---

## 5. 파이썬으로 구현

### 예제: 동전 거스름돈 문제

```python
def get_min_coins(change, coins):
    coins.sort(reverse=True)  # 큰 단위의 동전부터 정렬
    count = 0

    for coin in coins:
        count += change // coin  # 해당 동전으로 거슬러 줄 수 있는 개수
        change %= coin           # 남은 금액

    return count

# 테스트
coins = [500, 100, 50, 10]
change = 1260
print(get_min_coins(change, coins))  # 출력: 6
```

---

## 실습 문제

1. [백준 11047번: 동전 0](https://www.acmicpc.net/problem/11047)
2. [백준 1931번: 회의실 배정](https://www.acmicpc.net/problem/1931)
3. [백준 11399번: ATM](https://www.acmicpc.net/problem/11399)
4. [프로그래머스: 조이스틱](https://school.programmers.co.kr/learn/courses/30/lessons/42860)
5. [프로그래머스: 큰 수 만들기](https://school.programmers.co.kr/learn/courses/30/lessons/42883)
6. [프로그래머스: 구명보트](https://school.programmers.co.kr/learn/courses/30/lessons/42885)
7. [프로그래머스: 섬 연결하기](https://school.programmers.co.kr/learn/courses/30/lessons/42861)
8. [프로그래머스: 단속카메라](https://school.programmers.co.kr/learn/courses/30/lessons/42884)
9. [프로그래머스: 체육복](https://school.programmers.co.kr/learn/courses/30/lessons/42862)
10. [프로그래머스: 디스크 컨트롤러](https://school.programmers.co.kr/learn/courses/30/lessons/42627)
11. [백준 2457번: 공주님의 정원](https://www.acmicpc.net/problem/2457)
12. [백준 8980번: 택배](https://www.acmicpc.net/problem/8980)
13. [백준 1541번: 잃어버린 괄호](https://www.acmicpc.net/problem/1541)