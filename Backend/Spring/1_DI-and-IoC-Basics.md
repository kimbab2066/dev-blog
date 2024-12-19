# Spring Core: DI와 IoC 컨테이너

스프링의 핵심은 **DI(Dependency Injection)**와 **IoC(Inversion of Control)**입니다.  
스프링 컨테이너는 애플리케이션의 객체 생명 주기를 관리하며, 의존성을 자동으로 주입하여 개발 생산성을 높여줍니다.

---

## DI(Dependency Injection)란?  
의존성 주입은 **객체 간의 의존 관계를 스프링 컨테이너가 관리하도록 위임하는 것**을 의미합니다.

### 주요 DI 방식
1. **생성자 주입**: 객체 생성 시 의존성을 주입.  
2. **세터 주입**: 객체 생성 후 세터 메서드를 통해 의존성을 주입.  
3. **필드 주입**: 객체의 필드에 직접 주입 (`@Autowired`).

---

## IoC(Inversion of Control)란?  
IoC는 객체의 생성 및 관리를 개발자가 아닌 컨테이너가 담당하는 디자인 원칙입니다.  
스프링의 IoC 컨테이너는 객체를 생성하고, 의존성을 주입하며, 객체 생명주기를 관리합니다.

### IoC 컨테이너의 역할  
1. **객체 관리**: 객체 생성, 초기화, 소멸 관리.  
2. **의존성 주입**: 객체 간의 관계를 설정.  
3. **설정 관리**: `@Configuration` 또는 XML을 통해 빈 설정 관리.

---

## 스프링 컨테이너의 종류  
1. **BeanFactory**: 가장 기본적인 컨테이너 (사용 빈도 낮음).  
2. **ApplicationContext**: 더 많은 기능을 제공하는 컨테이너 (대부분 사용).  
   - 예: `ClassPathXmlApplicationContext`, `AnnotationConfigApplicationContext`.
