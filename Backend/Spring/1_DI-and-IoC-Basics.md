# DI(Dependency Injection)와 IoC(Inversion of Control) 기본 지식

스프링의 핵심 개념은 **DI(Dependency Injection)**와 **IoC(Inversion of Control)**입니다.  
이 두 가지는 객체 간의 의존성을 효과적으로 관리하고 애플리케이션의 확장성과 유연성을 높이는 데 기여합니다.

---

## 1. DI(Dependency Injection)

### 의존성 주입이란?
- **의존성**: 객체가 다른 객체를 사용하는 관계.
- **의존성 주입**: 객체가 필요한 의존성을 스스로 생성하지 않고, 외부에서 주입받는 방식.

### DI의 이점
1. **유연성**: 의존성 변경이 용이.
2. **테스트 용이성**: Mock 객체를 활용한 단위 테스트가 쉬워짐.
3. **유지보수성**: 의존성이 외부에 관리되므로 코드 변경이 최소화.

---

## 2. IoC(Inversion of Control)

### IoC란?
- 제어의 역전: 객체의 생성 및 생명주기 관리를 개발자가 아닌 **스프링 컨테이너**가 담당.

### IoC 컨테이너의 역할
1. 객체 생성 및 관리.
2. 의존성 주입 수행.
3. Bean의 생명주기 관리.

---

## 3. DI를 적용하지 않은 코드

```java
public class UserService {
    private UserRepository userRepository = new UserRepository();

    public void processUser() {
        // UserRepository를 직접 사용
        userRepository.saveUser();
    }
}
```

### 문제점
1. UserService는 UserRepository에 강하게 결합.
2. 확장성 및 테스트 용이성이 떨어짐.

---

## 4. DI를 적용한 코드

### 1) 생성자 주입
```java
@Component
public class UserService {
    private final UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

### 2) 필드 주입
```java
@Component
public class UserService {
    @Autowired
    private UserRepository userRepository;
}
```

### 3) 세터 주입
```java
@Component
public class UserService {
    private UserRepository userRepository;

    @Autowired
    public void setUserRepository(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

---

## 5. IoC 컨테이너에서의 동작

스프링 IoC 컨테이너는 객체를 생성하고, 의존성을 자동으로 주입합니다.  
Spring Boot 애플리케이션에서 이를 설정하는 기본 코드:

```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

---

## 6. 배운 점
- DI를 활용하면 객체 간의 결합도를 낮추고 코드의 유연성과 확장성을 높일 수 있습니다.
- IoC 컨테이너는 객체 생성 및 의존성 관리를 자동으로 처리합니다.
