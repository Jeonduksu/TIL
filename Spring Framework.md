# Spring Framework

## Spring Framework의 특징

---

* DI(Dependency Injection) 의존성 주입
  * Dao dao = new Dao(); => Dao dao;
  * 설정 파일이나 어노테이션을 통해 객체간의 의존 관계를 설정하여 
  * 개발자가 직접 의존하는 객체를 생성할 필요가 없다.
  * DL= Dependency Lookup
* Spring AOP(관점 지향 프로그래밍)
  - 트랜잭션,로깅,보안 등 여러 모듈, 여러 계층에서 공통으로 필요로 하는
    기능의 경우 해당 기능들을 분리하여 관리한다.
* POJO(Plain Old Java Object)
  - 일반적인 J2EE 프레임워크에 비해 특정 라이브러리를 사용할 필요가 없어
    개발이 쉬우며, 기존 라이브러리의 지원이 용이하다.
* IOC(Inversion of Control) 제어 반전
  * 컨트롤의 제어권이 개발자가 아니라 프레임워크에 있다는 뜻으로
    객체의 생성부터 모든 생명주기의 관리까지 프레임워크가 주도하고 있다.
  * 객체를 생성하고, 직접 호출하는 프로그램이 아니라, 만들어둔 자원을 호출해서 사용한다.
* Spring JDBC
  * Mybatis나 Hibernate 등의 데이터베이스를 처리하는 *영속성 프레임워크*와 연결할 수 있는
    인터페이스를 제공한다.
* Spring MVC
  * MVC 디자인 패턴을 통해 웹 어플리케이션의 Model, View, Controller 사이의 의존 관계를
    DI 컨테이너에서 관리하여 개발자가 아닌 서버가 객체들을 관리하는 웹 어플리케이션을 구축
    할 수 있다.
* PSA(Portable Service Abstarction)
  * 스프링은 다른 여러 모듈을 사용함에 있어 별도의 추상함에 레이어를 제공한다.
  * 예를 들어 JPA를 사용할 때에서 Spring JPA를 사용하여 추상화하므로 실제 구현에 있어서 
    Hibernate를 사용하든 EclipseLink를 사용하든 개발자는 이 모듈의 의존 없이
    프로그램에 집중할 수 있다.

## Spring의 구성 모듈

---

* Data 접근 계층
  * JDBC나 데이터베이스에 연결하는 모듈로, Data 트랜잭션에 해당하는 기능을 담당하여 
    영속성 프레임워크의 연결을 담당한다.
* Web 계층 (MVC/Remoting)
  * Spring Framework에서 Servlet, Struts 등 웹 구현 기술과의 연결점을 Spring MVC 구성으로 지원하기 위해 제공되는 모듈 계층이다.
  * 또한 스프링의 리모팅 기술로 RMI, Hessian,Burlap, JAX-WS, HTTP 호출자 그리고 REST API 모듈을 제공한다.
* AOP 계층
  * Spring에서 각 흐름 간 공통된 코드를 한 쪽으로 빼내어 필요한 시점에 해당 코드를 첨부하게 하기 위해 지원하는 계층으로, 별도의 proxy를 두어 동작한다. 이를 통해 객체간의 결합도를 낮출 수 있다.
* Core container
  * Spring의 핵심 부분이라고 할 수 있으며 모든 스프링 관련 모듈은 이 Core Container 기반으로 구축된다.
  * Spring의 근간이 되는 IoC 기능을 지원하는 영역을 담당하고 있다
  * BeanFactory를 기반으로 Bean클래스들을 제어할 수 있는 기능을 지원한다.



## Spring 모듈 정리

---

* spring-beans : 
  * 스프링 컨테이너를 이용해서 객체를 생성하는 기본기능을 제공
* spring-context : 
  * 객체생성, 라이프 사이클 처리, 스키마 확장 등의 기능을 제공
* spring-aop : 
  * AOP 기능을 제공
* spring-web : 
  * REST 클라이언트 데이터 변환처리, 서블릿 필터, 파일 업로드 지원 등 웹 개발에 필요한 기반 기능을 제공
* spring-webmvc : 
  * 스프링 기반의 MVC 프레임워크, 웹 애플리케이션을 개발하는데 필요한 컨트롤러, 뷰 구현을 제공
* spring-websocket : 
  * 스프링 MVC에서 웹 소켓 연동을 처리할 수 있도록 제공
* spring-oxm : 
  * XML과 자바 객체간의 매핑을 처리하기 위한 API 제공
* spring-tx : 
  * 트랜잭션 처리를 위한 추상 레이어를 제공
* spring-jdbc : 
  * JDBC 프로그래밍을 보다 쉽게 할 수 있는 템플릿 제공
* spring-orm :
  * Hibernate, JPA, Mybatis 등과의 연동을 지원
* spring-jms : 
  * JMS 서버와 메시지를 쉽게 주고 받을 수 있도록 하기 위한 템플릿
* spring-context-support
  * 스케쥴링, 메일방송, 캐시연동, 벨로시티 등 부가 기능을 제공

## Spring MVC 구성 요소

---

* DispatcherServlet
  * 클라이언트의 요청(resquest)을 전달 받고, 요청에 맞는 컨트롤러가 리턴 한 결과 값을
    view에 전달하여 알맞은 응답(response)을 생성
* HandlerMapping
  * 클라이언트의 요청 URL을 어떤 컨트롤러가 처리할지 결정
* Controller
  * 클라이언트의 요청을 처리한 뒤, 결과를 DispatcherServlet에게 리턴
* ModelAndView
  * 컨트롤러가 처리한 결과 정보 및 뷰 선택에 필요한 정보를 담음
* View Resolver
  * 컨트롤러의 처리 결과를 생성할 view를 결정
* View 
  * 컨트롤러의 처리 결과 화면을 생성,JSP 나 Velocity 템플릿 파일 등을 View로 사용