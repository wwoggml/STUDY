# Ch2 정리
### 마이크로서비스 아키텍처(MSA; Microservice Architecture)
``` 
💡 서비스 규모를 작게 나누어 구성한 아키텍처 
```

<br>
예를 들어, 포털 사이트를 블로그, 카페, 메일 등의 기능들을 하나의 애플리케이션에 넣어 개발하지 않고, 블로그 프로젝트, 카페 프로젝트, 메일 프로젝트 등 애플리케이션을 기능별로 나눠서 개발한다.   

###

<img src="https://user-images.githubusercontent.com/72512101/209678344-37ef2304-d216-45ca-94b7-fd9ca0823399.png" width="420" height="200">

단일 서비스로 구성된 포털 사이트는 내부 메서드를 호춣해 원하는 자원을 가져와 사용할 수 있지만
마이크로서비스와 같이 구성된 사이트에서 독립적인 애플리케이션을 개발하면 각 서비스 간에 통신해야 하는 경우가 발생한다. 

이런 상황에서 통신을 '**서버 간 통신**'이라고 말한다.      

###

#### 서버 간 통신
클라이언트에서 서버, 서버에서 클라이언트로 통신을 요청하는 것

→ 몇 가지 프로토콜에 의해 다양한 통신 방식을 적용할 수 있지만 가장 많이 사용되는 방식은 HTTP/HTTPS 방식이다.

###

<br>

<hr>

### 스프링 부트의 동작 방식
**서블릿(servlet)** 
```
💡 클라이언트의 요청을 처리하고 결과를 반환하는 자바 웹 프로그래밍 기술
   • 서블릿은 서블릿 컨테이너에서 관리한다.
```

**서블릿 컨테이너** 
```
💡 서블릿 인스턴스를 생성하고 관리하는 역할을 수행하는 주체
   ex) 톰캣
```

<br>

스프링 부트는 ```spring-boot-starter-web``` 모듈을 사용하기 때문에 기본적으로 톰캣을 사용하는 스프링 MVC 구조를 기반으로 동작한다.

* 일반적인 웹 요청이 들어왔을 때 스프링 부트의 동작 구조
<img src="https://user-images.githubusercontent.com/72512101/209681716-7a1964a3-d60f-4533-9d91-33f1ea1ab3c8.png"  width="50%" height="50%">

<br>


스프링에서는 DispatcherServlet이 서블릿의 역할을 수행한다.
1. DispatcherServlet으로 요청(HttpServletRequest)이 들어오면 핸들러 매핑을 통해 요청 URI에 매핑된 핸들러를 탐색한다. (핸들러 == 컨트롤러)
2. 핸들러 어댑터로 컨트롤러를 호출한다.
3. 핸들러 어댑터에 컨트롤러 응답이 돌아오면 ModelAndView 로 응답을 반환한다.
4. 뷰 형식으로 리턴하는 컨트롤러를 사용할 때는 뷰 리졸버를 통해 뷰를 받아 리턴한다.


###

<br>

<hr>

### 레이어드 아키텍처

```
💡 애플리케이션의 컴포넌트를 유사 관심사를 기준으로 레이어로 묶어 수평적으로 구성한 구조
```

* 일반적인 레이어드 아키텍처
  * 프레젠테이션 계층
  * 비즈니스 계층
  * 데이터 접근 계층



스프링 부트는 별도의 설정 없이 ```spring-boot-start-web```의 의존성을 사용할 때는 기본적으로 스프링 MVC 구조를 보인다.

<br>

**Spring MVC**

```
💡 Model-View-Controller
```

View, Controller → 프레젠테이션 계층 영역

Model → 비즈니스와 데이터 접근 계층 영역

* 스프링의 레이어드 아키텍처
  * 프레젠테이션 계층
  * 비즈니스 계층 → 서비스 배치(엔티티와 같은 도메인 객체의 비즈니스 로직 조합)
  * 데이터 접근 계층 → DAO(Repository)를 배치해 도메인 관리




###

<br>

<hr>

### REST API

**REST**
```
💡 Representational State Transfer 주고 받는 자원(Resource)에 이름을 규정하고 URI에 명시해 HTTP 메서드(GET, POST, PUT, DELETE)를 통해 해당 자원의 상태를 주고 받는 것
```

**API**
```
💡 Application Programming Interface, 애플리케이션에서 제공하는 인터페이스, API를 통해 서버 또는 프로그램 사이를 연결할 수 있다.
```

**REST API**
```
💡 REST 아키텍처를 따르는 시스템/애플리케이션 인터페이스
   REST 아키텍처를 구현하는 웹 서비스를 'RESTful 하다'라고 표현한다.
```

<br>


**REST의 URI 설계 규칙**

* URI의 마지막에는 '/'를 포함하지 않는다.

  http://localhost.com/product (o)
  
  http://localhost.com/product/ (x)
  
* 언더바(_) 대신 하이픈(-)을 사용한다.

  http://localhost.com/product-web-name (x)
  
* URI는 소문자로 쓴다.
* 파일의 확장자는 URI에 포함하지 않는다.
  
