# 스택(Stack) 개념 정리

스택(Stack)은 **후입선출(LIFO: Last In, First Out)** 방식으로 작동하는 데이터 구조입니다.  
즉, 가장 마지막에 추가된 데이터가 가장 먼저 제거됩니다.

---

## 1. 스택의 특징

1. **후입선출(LIFO)**: 마지막에 삽입된 데이터가 가장 먼저 제거됩니다.
2. **제한된 접근**: 데이터는 항상 스택의 **맨 위(top)** 에서만 추가(push)되거나 제거(pop)됩니다.
3. **두 가지 주요 연산**:
   - `push`: 데이터를 스택의 맨 위에 추가.
   - `pop`: 스택의 맨 위에 있는 데이터를 제거.

---

## 2. 스택의 동작 과정

### 예제
초기 상태: 스택이 비어 있음.

1. `push(1)` → 스택: `[1]`
2. `push(2)` → 스택: `[1, 2]`
3. `push(3)` → 스택: `[1, 2, 3]`
4. `pop()` → 제거된 데이터: `3`, 스택: `[1, 2]`

---

## 3. 스택의 활용

1. **수식 계산 및 괄호 검사**
   - 예: 수식에서 여는 괄호와 닫는 괄호의 균형 확인.
2. **재귀 함수의 실행**
   - 함수 호출 정보를 스택에 저장하여 실행 순서를 추적.
3. **Undo/Redo 기능**
   - 이전 작업 상태를 스택에 저장하여 되돌리기/다시 실행.
4. **웹 브라우저의 뒤로가기/앞으로가기**
   - 방문한 페이지를 스택에 저장.

---

## 4. 스택의 구현

### 1) **파이썬으로 구현**

#### 리스트를 사용한 스택 구현
```python
def push(stack, item):
    stack.append(item)

def pop(stack):
    if not is_empty(stack):
        return stack.pop()
    else:
        return "Stack is empty"

def is_empty(stack):
    return len(stack) == 0

def peek(stack):
    if not is_empty(stack):
        return stack[-1]
    else:
        return "Stack is empty"

# 테스트
stack = []
push(stack, 1)
push(stack, 2)
push(stack, 3)
print(stack)  # 출력: [1, 2, 3]
print(pop(stack))  # 출력: 3
print(stack)  # 출력: [1, 2]
```

---

## 5. 스택의 한계

1. **고정 크기 제한** (배열 기반 스택)
   - 배열을 사용하면 최대 크기가 고정됩니다.
2. **성능 문제**
   - 동적 배열의 크기 조정 시, 데이터 복사가 필요할 수 있습니다.

---

## 6. 스택과 큐의 비교

| 특성        | 스택(Stack)          | 큐(Queue)            |
|-------------|----------------------|---------------------|
| 접근 방식   | 후입선출 (LIFO)      | 선입선출 (FIFO)      |
| 주요 연산   | `push`, `pop`        | `enqueue`, `dequeue` |
| 사용 사례   | 재귀, Undo 기능      | 작업 대기열, BFS     |

---

## 실습 문제

1. [백준 10828번: 스택](https://www.acmicpc.net/problem/10828)
2. [백준 9012번: 괄호](https://www.acmicpc.net/problem/9012)
3. [백준 1874번: 스택 수열](https://www.acmicpc.net/problem/1874)
4. [백준 4949번: 균형잡힌 세상](https://www.acmicpc.net/problem/4949)
5. [백준 2493번: 탑](https://www.acmicpc.net/problem/2493)
6. [프로그래머스: 올바른 괄호](https://school.programmers.co.kr/learn/courses/30/lessons/12909)
7. [프로그래머스: 기능개발](https://school.programmers.co.kr/learn/courses/30/lessons/42586)
8. [프로그래머스: 프린터](https://school.programmers.co.kr/learn/courses/30/lessons/42587)
