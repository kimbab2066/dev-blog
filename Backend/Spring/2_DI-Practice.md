# Spring Core: DI 실습 예제

의존성 주입(DI)을 통해 객체 간의 의존성을 줄이고 유연성을 높이는 방법을 배웁니다.  
아래는 DI를 적용하지 않은 코드와 DI를 적용한 코드를 비교합니다.

---

## 1. DI 없이 작성한 코드

```java
class UserService {
    private UserRepository userRepository;

    public UserService() {
        this.userRepository = new UserRepository(); // 강한 결합
    }
}
```

### 문제점
- `UserService`는 `UserRepository`에 강하게 결합되어 있어 변경에 취약합니다.
- 유연성이 떨어져 테스트 작성 및 확장이 어렵습니다.

---

## 2. DI를 적용한 코드

### 1) **생성자 주입 방식**

```java
@Component
class UserService {
    private final UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

### 2) **필드 주입 방식**

```java
@Component
class UserService {
    @Autowired
    private UserRepository userRepository;
}
```

### 3) **세터 주입 방식**

```java
@Component
class UserService {
    private UserRepository userRepository;

    @Autowired
    public void setUserRepository(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

---

## 3. IoC 컨테이너에서의 의존성 주입

스프링의 IoC 컨테이너는 객체를 생성하고, 의존성을 자동으로 주입합니다.

### 애플리케이션 설정

```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

### 의존성 주입 테스트

```java
@RestController
class UserController {
    private final UserService userService;

    @Autowired
    public UserController(UserService userService) {
        this.userService = userService;
    }

    @GetMapping("/users")
    public List<User> getUsers() {
        return userService.getAllUsers();
    }
}
```

---

## 실습 문제

1. [DI와 IoC를 활용한 REST API 만들기](#)  
2. [Spring IoC 컨테이너에서 빈 관리 테스트](#)
