# Spring Core: To-Do 리스트 실전 사례

DI와 IoC 컨테이너를 활용하여 간단한 **To-Do 리스트 API**를 만들어봅니다.

---

## 1. 프로젝트 구조

아래는 To-Do 리스트 애플리케이션의 프로젝트 구조입니다:

```plaintext
src/main/java/com/example/todo/
├── controller/
│   └── ToDoController.java
├── service/
│   └── ToDoService.java
├── repository/
│   └── ToDoRepository.java
└── model/
    └── ToDo.java
```

---

## 2. 주요 코드

### 1) **To-Do 모델 클래스**

```java
@Entity
public class ToDo {
    @Id @GeneratedValue
    private Long id;
    private String task;
    private boolean completed;

    // Getters and Setters
    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getTask() {
        return task;
    }

    public void setTask(String task) {
        this.task = task;
    }

    public boolean isCompleted() {
        return completed;
    }

    public void setCompleted(boolean completed) {
        this.completed = completed;
    }
}
```

---

### 2) **Repository**

```java
@Repository
public interface ToDoRepository extends JpaRepository<ToDo, Long> {}
```

---

### 3) **Service**

```java
@Service
public class ToDoService {
    private final ToDoRepository toDoRepository;

    @Autowired
    public ToDoService(ToDoRepository toDoRepository) {
        this.toDoRepository = toDoRepository;
    }

    public List<ToDo> getAllTasks() {
        return toDoRepository.findAll();
    }

    public ToDo createTask(ToDo toDo) {
        return toDoRepository.save(toDo);
    }

    public void deleteTask(Long id) {
        toDoRepository.deleteById(id);
    }
}
```

---

### 4) **Controller**

```java
@RestController
@RequestMapping("/todos")
public class ToDoController {
    private final ToDoService toDoService;

    @Autowired
    public ToDoController(ToDoService toDoService) {
        this.toDoService = toDoService;
    }

    @GetMapping
    public List<ToDo> getAllToDos() {
        return toDoService.getAllTasks();
    }

    @PostMapping
    public ToDo createToDo(@RequestBody ToDo toDo) {
        return toDoService.createTask(toDo);
    }

    @DeleteMapping("/{id}")
    public void deleteToDo(@PathVariable Long id) {
        toDoService.deleteTask(id);
    }
}
```

---

## 3. 실행 및 테스트

### 1) **애플리케이션 실행**
- `SpringApplication.run(Application.class, args);`를 통해 실행합니다.

### 2) **Postman으로 테스트**
1. **GET /todos**: 모든 To-Do 리스트 가져오기.  
2. **POST /todos**: 새로운 To-Do 추가.  
   - Request Body:
     ```json
     {
       "task": "Learn Spring",
       "completed": false
     }
     ```
3. **DELETE /todos/{id}**: To-Do 삭제.

---

## 실습 문제

1. To-Do 리스트를 **완료 상태로 변경하는 API**를 추가하세요.  
2. **페이징 처리**를 도입하여 대량의 데이터를 효율적으로 가져오세요.
