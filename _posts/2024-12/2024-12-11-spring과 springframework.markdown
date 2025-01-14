---
title: TIL(20241211) [Spring & SpringBoot]
author: hanni
date: 2024-12-11 14:50:00 +0800
categories: TIL
tags: [Library, Framework]
---

----------------------------------------------------------------------------

먼저 프레임워크와 라이브러리의 개념이 혼란스러울 때가 있어 둘 개념을 확실하게 잡고 가고자 한다. 

## 💡 프레임워크 란?
- 소프트웨어 개발을 수월하게 하기 위한 소프트웨어 개발 환경(일하기 위한 틀을 제공(?))
- 장점 : 개발 효율성이 높아진다.
- 단점 : 정해진 틀에서 개발

## 💡 라이브러리 란?
- 어플리케이션에 필요한 클래스, 함수 등을 모아놓는 코드의 모음
- 개발자가 필요에 따라 원하는 기능을 구현하기 위한 코드의 모음으로 일종의 도구 역할

## ✨ 프레임워크 VS 라이브러리
- 프레임워크는 어플리케이션을 개발할 때 전체적인 구조를 잡기 위해 사용하는 것
- 라이브러리는 개발을 하는 과정에서 필요한 기능을 구현하기 위해 사용하는 것

----------------------------------------------------------

## 💡 Spring framework

- 오픈 소스 프레임워크로 enterpise용 JAVA 어플리케이션 개발을 편하게 할 수 있게 도와주는 경량급 어플리케이션 프레임 워크
- 소프트웨어가 많이 발전한 이 시점에서 많은 사용자의 요청을 동시에 처리해야 하기에 서버 성능/안전성/보안이 중요하다. 하지만 이런 것들을 다 신경쓰면서 개발하기는 쉽지 않기 때문에 Spring framework는 엔터프라이즈 어플리케이션을 위한 개발 환경을 제공해서 기능 개발에 집중할 수 있도록 도와주는 도구이다. 
- 개발 초기 기본 설정과 적용시킬 기술을 잘 선택한다면, 기술보다는 어플리케이션 로직자체에 집중해서 비지니스 로직을 구현할 수 있다.
- 주요 특징 : POJO(순수 자바 객체), AOP(관점지향 프로그래밍: 핵심관점/부가관점), IoC(제어의 역전), DI(의존성 주입), 빈 생명주기 관리
```
Enterprise Application ?
- 대규모의 복잡한 데이터를 관리하는 어플리케이션
```

### 📌 IoC(Inversion of Control)와 DI(Dependency Injection)

#### IoC
- 직역하면 "제어의 역전"
- 개발자가 직접 객체를 생성하고 관리하는 것이 아닌 스프링 컨테이너가 객체의 생성과 생명 주기 관리를 담당
- 즉, "누가 객체를 생성할지"에 대한 제어권이 개발자가 아닌 컨테이너에게 넘어간다. 
- 코드의 결합도를 낮추고 유지 보수성을 향상시킬 수 있음

#### DI
- "의존성 주입"
- 객체 간의 의존 관계를 컨테이너가 자동으로 관리하고 주입해주는 방식
- 객체간의 의존성을 외부에서 주입하는 방식(생성자 주입, Setter주입 등)

```
public class A {
    b = new B(); // A클래스에서 new 키워드로 클래스 B의 객체를 생성함
}

```

- 위에서 자바코드를 작성해 객체를 생성할 때는 객체가 필요한 곳에 직접 생성했다.

```
public class A {
    private B b;

    public A (B b) { // 외부에서 B객체를 주입 받는 방식
        this.b = b;
    }
}
```

- A 클래스는 B객체를 직접 생성하지 않고 외부에서 B객체를 주입받는 방식(생성자 주입)


#### 즉, IoC와 DI는 결합도를 감소시켜 객체들이 서로 간섭하지 않도록 하며, 코드의 확장성과 유지보수성 그리고 테스트 용이성을 향상시킬 수 있다. 


### 📌 AOP (관점 지향 프로그래밍)
- 프로그래밍에 대한 관심을 핵심 관점, 부가 관점으로 나누어서 관심 기준으로 모듈화하는 것을 의미함
- 예를 들어 계좌이체, 고객 관리하는 프로그램이 있을 때 각 프로그램에는 로깅, 데이터베이스 연결로직이 포함 될텐데 이 때 **핵심관점**은 계좌이체, 고객관리 로직이고 **부가관점** 로깅, 데이터베이스 연결 로직이 된다. 여기에 AOP 관점을 적용하면
부가관점에 해당하는 로직을 모듈화하게 되면 부가 관점 코드와 핵심 관점 코드를 분리하여 개발자에게 핵심 관점 코드에만 집중할 수 있게 도와준다. 
- 장점 : 개발자에게 핵심 관점 코드에 집중할 수 있도록 지원, 프로그램 변경 확장에도 유연하게 대응 가능하다.



## 💡 SpringBoot
- SpringBoot는 Springframework를 보다 쉽게 사용할 수 있도록 Springframework를 기반 한 도구이다. SpringBoot는 개발자가 설정파일을
작성할 필요 없이, 프로젝트 설정과 라이브러리 의존성을 자동으로 처리해주는 기능을 제공한다. 또한 Spring boot는 실행 가능한 JAR파일을
만들 수 있다.  
- 예를들어, Spring Boot는 Spring MVC, Spring Data JPA, Spring Security 등의 기능을 자동으로 설정
- 핵심 기능 : 내장서버(WAS), 자동 라이브러리 관리, 자동구성, 외부설정, 모니터링 & 관리기능


