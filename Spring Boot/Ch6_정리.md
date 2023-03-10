# 데이터베이스 연동


### 1️⃣ ORM
```
💡 ORM(Object Relational Mapping)은 객체 관계 매핑을 의미한다.
   자바와 같은 객체지향 언어에서 의미하는 객체와 RDB(Relational Database)의 테이블을 자동으로 매핑하는 방법이다.
```

위에서 말한 객체는 클래스를 의미한다. <br>
클래스는 데이터베이스의 테이블과 매핑하기 위해 만들어진 것이 아니기 때문에 RDB 테이블과 어쩔 수 없는 불일치가 존재한다.

<br>


ORM은 이 둘의 불일치와 제약사항을 해결하는 역할이다.

<img src="https://user-images.githubusercontent.com/72512101/211353592-ea16e344-d81e-4445-86f0-322afeaa7058.png" style="width:50%; height:50%">

ORM을 이용하면 쿼리문 작성이 아닌 코드(메서드로)로 데이터를 조작할 수 있다.

<br>


#### ORM의 장점
* 데이터베이스 쿼리를 객체지향적으로 조작할 수 있다
* 재사용 및 유지보수 편리
  * ORM을 통해 매핑된 객체는 모두 독립적으로 작성되어 있어 재사용이 용이하다
  * 객체들은 각 클래스로 나뉘어 있어 유지보수가 수월하다.
* 데이터베이스에 대한 종속성이 줄어든다.
  * ORM을 통해 자동 생성된 SQL문은 객체를 기반으로 데이터베이스 테이블을 관리하기 때문에 데이터베이스에 종속적이지 않다.



#### ORM의 단점
* ORM만으로 온전한 서비스를 구현하기에는 한계가 있다.
  * 복잡한 서비스의 경우 직접 쿼리를 구현하지 않고 코드로 구현하기 어렵다
  * 복잡한 쿼리를 정확한 설계 없이 ORM만으로 구성하게 되면 속도 저하 등의 성능 문제가 발생할 수 있다.
* 애플리케이션의 객체 관점과 데이터베이스의 관계 관점의 불일치가 발생한다.


<br>

### 2️⃣ JPA
```
💡 JPA(Java Persistence API)는 자바 진영의 ORM 기술 표준으로 채택된 인터페이스의 모음이다.
   ORM > JPA, ORM이 더 큰 개념이다. JPA는 더 구체적인 스펙을 포함한다.
```
JPA 또한 실제로 동작하는 것이 아니라 어떻게 동작해야 하는지 메커니즘을 정리한 표준 명세로 생각하면 된다.

<img src="https://user-images.githubusercontent.com/72512101/211355909-c3dd91f1-1186-4d77-a846-42eb2e3d23fd.png" style="width:50%; height:50%">


<br>

JPA는 내부적으로 `JDBC`를 사용한다. <br>
JPA는 개발자가 직접 JDBC를 구현하는 문제점을 보완하여 개발자 대신 적절한 SQL을 생성하고 데이터베이스를 조작해 객체를 자동 매핑하는 역할을 수행한다.


#### JPA 기반의 구현체
* 하이버네이트(Hibernate)
* 이클립스 링크(EclipseLink)
* 데이터 뉴클리어스(DataNucleus)


<br>

### 3️⃣ Hibernate
```
💡 자바의 ORM 프레임워크로, JPA가 정의하는 인터페이스를 구현하고 있는 JPA 구현체 중 하나다.
```
* 스프링 부트에는 하이버네이트의 기능을 더욱 편리하게 사용하도록 모듈화한 Spring Data JPA가 존재한다.


#### Spring Data JPA
```
💡 JPA를 편리하게 사용할 수 있도록 지원하는 스프링 하위 프로젝트 중 하나
```
* CRUD 처리에 필요한 인터페이스 제공
* 하이버네이트의 엔티티 매니저를 직접 다루지 않고 리포지토리를 정의해 사용하여 스프링이 적합한 쿼리를 동적으로 생성하는 방식으로 데이터베이스를 조작한다.

<img src="https://user-images.githubusercontent.com/72512101/211357670-7f599cc8-d0ed-4261-ad0e-23866e8c1594.png" style="width:50%; height:50%">


<br>

### 4️⃣ 영속성 컨텍스트
```
💡 영속성 컨텍스트(Persistence Context)는 애플리케이션과 데이터베이스 사이에서 엔테티와 레코드의 괴리를 해소하는 기능과 객체를 보관하는 기능을 수행한다.
```

엔티티 객체가 영속성 컨텍스트에 들어오면 JPA는 엔티티 객체의 매핑 정보를 데이터베이스에 반영하는 작업을 수행한다. <br>
* 영속 객체(Persistence Object) : 엔티티 객체가 영속성 컨텍스트에 들어와 JPA의 관리 대상이 되는 시점부터의 해당 객체


#### 엔티티 매니저
```
💡 엔티티를 관리하는 객체
```

* 엔티티 매니저는 엔티티 매니저 팩토리가 만든다.
* 엔티티 매니저 팩토리 : 데이터베이스에 대응하는 객체로서 스프링 부트에서는 자동 설정 기능이 있기 때문에 application.properties에서 작성한 최소한의 설정만으로 동작한다.

* 엔티티 매니저 팩토리로 생성된 엔티티 매니저는 엔티티를 영속성 컨텍스트에 추가해서 영속 객체로 만드는 작업을 수행하고, 영속성 컨텍스트와 데이터베이스를 비교하면서 실제 데이터베이스를 대상으로 작업을 수행한다.


#### 엔티티의 생명주기
* 비영속 : 영속성 컨텍스트에 추가되지 않은 엔티티 객체 상태
* 영속 : 영속성 컨텍스트에 의해 엔티티 객체가 관리되는 상태
* 준영속 : 영속성 컨텍스트에 의해 관리되던 엔티티 객체가 컨텍스트와 분리된 상태
* 삭제 : 데이터베이스에서 레코드를 삭제하기 위해 영속성 컨텍스트에 삭제 요청을 한 상태

<br>

### 5️⃣ 데이터베이스 연동

#### application.properties 파일에 데이터베이스 관련 설정 추가하기

```properites
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver
spring.datasoure.url=jdbc:mariadb://localhost:3306/springboot
spring.datasource.username=root
spring.datasource.password=smjj1418**

spring.jpa.hibernate.ddl-auto=create
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```
* `spring.datasource.driver-class-name` : 연동하려는 데이터베이스의 드라이버 정의
* `spring.datasoure.url` : 마리아DB의 경로 명시, 경로와 데이터베이스명 정의
* `spring.datasource.username`, `spring.datasource.password` : 데이터베이스 계정 정보
* `spring.jpa.hibernate.ddl-auto` : 데이터베이스를 자동으로 조작하는 옵션, create는 기존 테이블을 지우고 새로 생성하는 것이다.
* `spring.jpa.show-sql` : 로그에 하이버네이트가 생성한 쿼리문 출력
* `spring.jpa.properties.hibernate.format_sql` : 보기 좋게 포맷


<br>


### 6️⃣ 엔티티 설계
* Spring Data JPA를 사용하면 데이터베이스에 테이블을 생성하기 위해 직접 쿼리를 작성할 필요가 없다. 이 기능을 가능하게 하는 것이 엔티티이다.
* JPA에서 엔티티는 데이터베이스의 테이블에 대응하는 클래스이다.
* 엔티티에는 데이터베이스에 쓰일 테이블과 칼럼을 정의한다.
* 엔티티에 어노테이션을 사용하면 테이블 간의 연관관계를 정의할 수 있다.


#### 엔티티 관련 기본 어노테이션
* `@Entity` : 해당 클래스가 엔티티임을 명시하는 어노테이션
* `@Table` : 엔티티 클래스는 테이블과 일대일로 매칭되므로 @Table 어노테이션은 필요없지만 클래스의 이름과 테이블의 이름을 다르게 지정하고 싶은 경우 @Table(name = 값) 형태로 테이블 명을 정한다.
* `@Id` : 엔티티 클래스의 필드는 테이블의 칼럼과 매핑된다. <br>   @Id 어노테이션을 사용하면 테이블의 기본값 역할로 사용된다.
   * 모든 엔티티는 @Id 어노테이션이 필요하다.
* `@GeneratedValue` : 해당 필드의 값을 어떤 방식으로 자동으로 생성할지 결정한다. <br> @Id 어노테이션과 함께 사용한다.
   * 사용하지 않는 경우 : 애플리케이션에서 자체적으로 고유한 기본값을 생성할 경우 사용, 내부에 정해진 규칙에 의해 기본값을 생성하고 식별자로 사용한다.
   * `AUTO` : 기본 설정값으로 기본값을 사용하는 데이터베이스에 맞게 자동 생성한다.
   * `IDENTITY` : 기본값 생성을 데이터베이스에 위임한다. <br> 데이터베이스 AUTO_INCREMENT를 사용해 기본값을 생성한다
   * `SEQUENCE` : @SequenceGenerator 어노테이션으로 식별자 생성기를 설정하고 이를 통해 값을 자동 주입받는다.
   * `TABLE` : 어떤 DBMS를 사용하더라도 동일하게 동작한다. 식별자로 사용할 숫자의 보관 테이블을 별도로 생성한다
* `@Column` : 필드에 설정을 더할 때 사용
   * name : 칼럼명 설정
   * nullable : null 처리가 가능한지 명시
   * length : 저장하는 데이터의 최대 길이 설정
   * unique : 해당 칼럼을 유니크로 설정
* `@Transient` : 엔티티 클래스에는 선언되어 있지만 데이터베이스에서는 필요 없을 경우 사용

<br>

### 7️⃣ 리포지토리 인터페이스 설계
Spring Data JPA는 JpaRepository를 기반으로 더욱 더 쉽게 사용할 수 있다. <br>
**첫 단어를 제외한 이후 단어들의 첫 글자를 대문자로 설정하면 JPA에서 인식하고 쿼리를 자동으로 만들어준다.**

ex) findByName(String name), findByNameAndEmail(String name, String email) 등
* findBy는 SQL문의 where 절 역할이다.
* And/Or
* Like/NotLike
* countBy
* orderBy

위의 조건 외에도 여러가지 조건들이 있다.


<br>


### 8️⃣ DAO 설계
```
💡 DAO(Data Access Object) : 데이터베이스에 접근하기 위한 로직을 관리하는 객체
```
Spring Data JPA 에서 DAO 개념은 리포지토리가 대체한다.

* DAO를 서비스 레이어와 리포지토리의 중간 계층을 구성하는 역할로 사용한다.
* DAO 클래스는 일반적을 '인터페이스-구현체' 구성으로 생성한다.


<br>

> __Note__
> 
> 클래스를 스프링이 관리하는 빈으로 등록하려면 `@Component` 또는 `@Service` 어노테이션을 지정해야 한다.  <br>
> 빈으로 등록된 객체는 다른 클래스가 인터페이스를 가지고 의존성을 주입받을 때 이 구현체를 찾아서 주입하게 된다.

* DAO 객체에서도 데이터베이스에 접근하기 위해 리포지토리 인텊이스를 사용해 의존성 주입(생성자를 통해)을 받아야 한다.

<br>

> __Note__
> 
> 빌더 메서드는 빌더(Builder) 패턴을 따르는 메서드이다. <br>
> 데이터 클래스를 사용할 때 생성자로 초기화할 경우 모든 필드에 값을 넣거나 null을 명시적으로 사용해야 하는데, 이러한 단점을 보완하기 위해 나온 패턴이 빌더 패턴이다.
> 빌더 패턴을 이용하면 필요한 데이터만 설정할 수 있어 유연성을 확보할 수 있다.
