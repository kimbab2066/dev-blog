# Spring Data JPA로 데이터베이스 연결

Spring Data JPA는 데이터베이스와의 상호작용을 간소화하며, 표준 JPA(Java Persistence API)를 기반으로 한 강력한 프레임워크입니다.  
이 문서에서는 간단한 CRUD 애플리케이션을 작성하며 Spring Data JPA의 주요 기능을 배웁니다.

---

## 1. 프로젝트 설정

### 1) **Gradle 설정**

`build.gradle` 파일에 다음 종속성을 추가합니다:
```groovy
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    runtimeOnly 'com.h2database:h2'
    implementation 'org.projectlombok:lombok'
    annotationProcessor 'org.projectlombok:lombok'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```

### 2) **application.properties**

H2 데이터베이스를 사용하기 위한 설정을 추가합니다:
```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driver-class-name=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.show-sql=true
spring.h2.console.enabled=true
```

---

## 2. 주요 코드

### 1) **엔티티 클래스**

Lombok 어노테이션을 사용하여 코드를 간결하게 작성합니다:

```java
import jakarta.persistence.*;
import lombok.*;

@Entity
@Data
@Builder
@AllArgsConstructor
@NoArgsConstructor
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private String email;
}
```

---

### 2) **Repository**

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface UserRepository extends JpaRepository<User, Long> {}
```

---

### 3) **Service**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class UserService {
    private final UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public List<User> getAllUsers() {
        return userRepository.findAll();
    }

    public User saveUser(User user) {
        return userRepository.save(user);
    }

    public void deleteUser(Long id) {
        userRepository.deleteById(id);
    }
}
```

---

### 4) **Controller**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/users")
public class UserController {
    private final UserService userService;

    @Autowired
    public UserController(UserService userService) {
        this.userService = userService;
    }

    @GetMapping
    public List<User> getAllUsers() {
        return userService.getAllUsers();
    }

    @PostMapping
    public User createUser(@RequestBody User user) {
        return userService.saveUser(user);
    }

    @DeleteMapping("/{id}")
    public void deleteUser(@PathVariable Long id) {
        userService.deleteUser(id);
    }
}
```

---

## 3. 실행 및 테스트

### 1) **H2 콘솔 확인**
- 브라우저에서 `http://localhost:8080/h2-console` 접속.
- JDBC URL: `jdbc:h2:mem:testdb`

### 2) **Postman 테스트**
1. **GET /users**: 모든 사용자 가져오기.  
2. **POST /users**: 새 사용자 생성.  
   - Request Body:
     ```json
     {
       "name": "John Doe",
       "email": "john.doe@example.com"
     }
     ```
3. **DELETE /users/{id}**: 사용자 삭제.

---

## 실습 문제

1. **PUT API**를 추가하여 사용자 정보를 업데이트하세요.  
2. 이메일로 사용자를 검색하는 **Custom Query**를 추가하세요.
