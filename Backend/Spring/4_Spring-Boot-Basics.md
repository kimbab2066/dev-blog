# Spring Boot Basics: 기본 설정 및 REST API 생성

Spring Boot는 스프링 애플리케이션 개발을 단순화하기 위한 강력한 프레임워크입니다.  
이 문서에서는 Spring Boot의 기본 설정과 REST API를 구현하는 방법을 배웁니다.

---

## 1. Spring Boot 기본 설정

### 1) **Gradle 프로젝트 생성**

Spring Initializr를 통해 Gradle 프로젝트를 생성합니다.  
다음 종속성을 포함하세요:
- Spring Web
- Spring Boot DevTools

#### `build.gradle` 예시:
```groovy
plugins {
    id 'org.springframework.boot' version '3.1.0'
    id 'io.spring.dependency-management' version '1.1.0'
    id 'java'
}

group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '17'

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    developmentOnly 'org.springframework.boot:spring-boot-devtools'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```

---

## 2. 간단한 REST API 만들기

### 1) **컨트롤러 클래스 생성**

`HelloController`를 작성하여 간단한 `Hello World` API를 생성합니다.

```java
@RestController
@RequestMapping("/api")
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, Spring Boot!";
    }
}
```

---

### 2) **애플리케이션 실행**

#### **Application 클래스**
Spring Boot 애플리케이션의 진입점입니다.

```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

---

### 3) **Postman 테스트**

1. **GET /api/hello**
   - URL: `http://localhost:8080/api/hello`
   - 응답: `"Hello, Spring Boot!"`

---

## 3. Spring Boot DevTools 사용

Spring Boot DevTools는 개발 중에 애플리케이션을 자동으로 다시 로드하는 기능을 제공합니다.  
`build.gradle` 파일에 `developmentOnly`로 추가되어 있어 자동 활성화됩니다.

---

## 실습 문제

1. 간단한 **POST API**를 추가하여 데이터를 받아 처리해 보세요.  
2. API에 요청 매개변수를 추가하고, 조건에 따라 다른 응답을 반환하도록 수정하세요.
