### 1๏ธโฃ GET API
```
๐ก GET API๋ ์น ์ ํ๋ฆฌ์ผ์ด์ ์๋ฒ์์ ๊ฐ์ ๊ฐ์ ธ์ฌ ๋ ์ฌ์ฉํ๋ API์ด๋ค.
```


<br>


* ```@RestController```์ ```@Controller```์ ```@ResponseBody```๊ฐ ๊ฒฐํฉ๋ ์ด๋ธํ์ด์์ผ๋ก, ํด๋์ค์ RestController๋ฅผ ๋ถ์ด๋ฉด ํ์ ๋ฉ์๋์ ```@ResponseBody```๋ฅผ ๋ถ์ด์ง ์์๋ ๋ฌธ์์ด๊ณผ JSON ๋ฑ์ ์ ์กํ  ์ ์๋ค.
* ```@RequesetMapping```์ ์๋ฒ์ URL๊ณผ ํน์  ์ฒ๋ฆฌ๋ฅผ ์ฐ๋(๋งคํ)์ํค๋ ๊ตฌ์กฐ์ด๋ค.

<br>

**RestController๊ณผ Controller์ ์ฐจ์ด์ **

* ```@Controller```์ Model๊ฐ์ฒด๋ฅผ ๋ง๋ค์ด ๋ฐ์ดํฐ๋ฅผ ๋ด๊ณ  View๋ฅผ ์ฐพ์ง๋ง, ```@RestController```์ ๋จ์ํ ๊ฐ์ฒด๋ง์ ๋ฐํํ๊ณ  ๊ฐ์ฒด ๋ฐ์ดํฐ๋ JSON ๋๋ XML ํ์์ผ๋ก HTTP ์๋ต์ ๋ด์์ ์ ์กํ๋ค.


```
๐กREST(Representational State Transfer)๋?
  HTTP URI(Uniform Resource Identifier)๋ฅผ ํตํด ์์(Resource)์ ๋ช์ํ๊ณ 
  HTTP Method(POST, GET, PUT, DELETE, PATCH ๋ฑ)๋ฅผ ํตํด
  ํด๋น ์์(URI)์ ๋ํ CRUD Operation์ ์ ์ฉํ๋ ๊ฒ์ ์๋ฏธํฉ๋๋ค.
  ๊ทธ๋ฆฌ๊ณ  ์ด๋ฌํ ๊ฒ๋ค์ ์ค์ํ์ ๋ ๊ทธ ์์คํ์ RESTfulํ๋ค๊ณ  ํ๋ค.
  
  REST์ ๊ฒฝ์ฐ ํด๋ผ์ด์ธํธ๊ฐ ํน์  URL์ ์ ์ํ๋ฉด ์น ํ์ด์ง๋ฅผ ๊ทธ๋ฆฌ๋ ๊ฒ์ด ์๋๋ผ ํน์  ์ ๋ณด ๋๋ ํน์  ์ฒ๋ฆฌ ๊ฒฐ๊ณผ๋ฅผ ํ์คํธ ํํ๋ก ๋ฐํํ๋ค.
```


<br>

**์์ **

```java
package com.example.spring.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {
    @RequestMapping(value = "/spring", method = RequestMethod.GET)
    public String getSpring() {
        return "Hello API!";
    }
}
```



<br>

**๊ฒฐ๊ณผ**

![แแณแแณแแตแซแแฃแบ 2023-01-08 แแฉแแฅแซ 12 53 24](https://user-images.githubusercontent.com/72512101/211159361-56924aaa-8e99-4924-bc16-01b838763c36.png)

<br>


๐จ ์คํ๋ง4.3 ๋ฒ์  ์ดํ๋ก๋ @GetMapping, @PostMapping, @PutMapping, @DeleteMapping ์ ์ฌ์ฉํ๊ธฐ ๋๋ฌธ์ ํน๋ณํ ๊ฒฝ์ฐ๊ฐ ์๋๋ฉด @RequestMapping์ ์ ์ฌ์ฉํ์ง ์๋๋ค.

<br>


์๋ ์ฝ๋๋ ์์ ์ฝ๋๋ฅผ @RequestMapping ๋์  @GetMapping์ ์ฌ์ฉํ์ฌ ๊ตฌํํ ๊ฒ์ผ๋ก ๊ฒฐ๊ณผ๋ ์์ ๋๊ฐ๋ค.


```java
package com.example.spring.controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {

    @GetMapping(value = "/spring")
    public String getSpring2() {
        return "Hello API!";
    }
}
```

<br>


#### @PathVariable
@GetMapping ์ ๋ณ๋์ ๋งค๊ฐ๋ณ์ ์์ด GET API๋ฅผ ๊ตฌํํ๋ ๊ฒ์ด๊ณ , ๋งค๊ฐ๋ณ์๋ฅผ ๋ฐ๊ธฐ ์ํด์๋ URL ์์ฒด์ ๊ฐ์ ๋ด์ ์์ฒญํ๋ ๋ฐฉ๋ฒ์ด ์๋ค.
```@PathVariable``` ์ ์ฌ์ฉํ์ฌ ์ฟผ๋ฆฌ ํ์์ผ๋ก ๊ฐ์ ์ ๋ฌํ๋ ๊ฒ์ด ์๋ URL ํจ์ค๋ก ํ๋ผ๋ฏธํฐ๋ฅผ ์ ๋ฌํ์ฌ ์ฌ์ฉํ๋ค.




```java
package com.example.spring.controller;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {

    @GetMapping(value = "/spring/{variable}")
    public String getVariable(@PathVariable String variable) {
        return variable;
    }
}
```

<br>

์ฃผ์์ฐฝ์ http://localhost:8080/api/v1/get-api/spring/hello ์ ์๋ ฅํ๋ฉด @GetMapping์ ์ค๊ดํธ{} ์์น์ ๋งค๊ฐ๋ณ์๋ก hello๊ฐ ์ ๋ฌ๋๊ณ  ํ๋ฉด์ hello๊ฐ ์ถ๋ ฅ๋๋ค. 

![แแณแแณแแตแซแแฃแบ 2023-01-08 แแฉแแฅแซ 1 05 00](https://user-images.githubusercontent.com/72512101/211159803-6fb597b8-d1cc-41ce-b272-f06b3fdbaece.png)


<br>




#### @RequestParam

์์์ ์ธ๊ธํ ```@PathVariable```์ URL ๊ฒฝ๋ก์ ๊ฐ์ ๋ด์ ์์ฒญ์ ๋ณด๋ด๋ ๋ฐฉ๋ฒ์ด๊ณ , ```@RequestParam```์ ์ฟผ๋ฆฌ ํ์์ผ๋ก ๊ฐ์ ์ ๋ฌํ๋ ๊ฒ์ด๋ค.

* ์ฟผ๋ฆฌ ํ์์ URI์์ '?'๋ฅผ ๊ธฐ์ค์ผ๋ก 'ํค=๊ฐ' ํํ๋ก ๊ตฌ์ฑ๋ ์์ฒญ์ ์ ์กํ๋ ๋ฐฉ๋ฒ์ด๋ค.


<br>


**์ฝ๋**

```java
package com.example.spring.controller;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {

    @GetMapping(value = "/request")
    public String getRequestParam(@RequestParam String name, @RequestParam String email) {
        return name + " " + email;

    }
}
```

<br>

url์ ์๋ ฅํ ๊ฒ์ ๋ณด๋ฉด '?' ์ค๋ฅธ์ชฝ์ผ๋ก 'ํค=๊ฐ' ํ์์ผ๋ก ์ฟผ๋ฆฌ์คํธ๋ง์ด ๋ช์๋์ด ์๋ค. ๋งค๊ฐ๋ณ์๋ฅผ ์ฌ๋ฌ ๊ฐ ๋ฐ์ผ๋ ค๋ฉด '&'๋ฅผ ์ฌ์ฉํ์ฌ ๋ณ์ ์ฌ๋ฌ ๊ฐ๋ฅผ ์ ๋ฌ ๋ฐ๋๋ค.

<img width="762" alt="แแณแแณแแตแซแแฃแบ 2023-01-08 แแฉแแฅแซ 1 18 36" src="https://user-images.githubusercontent.com/72512101/211160364-2ec67003-af58-4d83-9911-df9462c79cee.png">


<br>


### 2๏ธโฃ DTO

```
๐ก Data Transfer Object, ๊ฐ ํด๋์ค ๋ฐ ์ธํฐํ์ด์ค๋ฅผ ํธ์ถํ๋ฉด์ ์ ๋ฌํ๋ ๋งค๊ฐ๋ณ์๋ก ์ฌ์ฉ๋๋ ๋ฐ์ดํฐ ๊ฐ์ฒด
   ๋ค๋ฅธ ๋ ์ด์ด ๊ฐ์ ๋ฐ์ดํฐ ๊ตํ์ ํ์ฉํ๋ค. 
```

<br>


```java
package com.example.spring.dto;

public class MemberDto {
    private String name;
    private String age;
    private String email;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getAge() {
        return age;
    }

    public void setAge(String age) {
        this.age = age;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    @Override
    public String toString() {
        return "MemberDto{" +
                "name='" + name +'\'' +
                ", age='" + age + '\'' +
                ", email='" + email + '\'' + "}";
    }
}
```

<br>

```java
@GetMapping(value = "/request3")
public String getRequestParam3(MemberDto memberDto) {
   return memberDto.toString();
}
```    


<br>


### 3๏ธโฃ POST API
```
๐ก ์ ์ฅํ๊ณ ์ ํ๋ ๋ฆฌ์์ค๋ ๊ฐ์ HTTP ๋ฐ๋์ ๋ด์ ์๋ฒ์ ์ ๋ฌํ๋ค.
```

```@RequestBody```๋ HTTP์ Body ๋ด์ฉ์ ํด๋น ์ด๋ธํ์ด์์ด ์ง์ ๋ ๊ฐ์ฒด์ ๋งคํํ๋ ์ญํ ์ ํ๋ค.


<br>


### 4๏ธโฃ PUT API
```
๐ก ์น ์ ํ๋ฆฌ์ผ์ด์ ์๋ฒ๋ฅผ ํตํด ๋ฐ์ดํฐ๋ฒ ์ด์ค ๊ฐ์ ์ ์ฅ์์ ์กด์ฌํ๋ ๋ฆฌ์์ค ๊ฐ์ ์๋ฐ์ดํธ ํ๋ ๋ฐ ์ฌ์ฉํ๋ค.
```


<br>


### 5๏ธโฃ ๋กํน ๋ผ์ด๋ธ๋ฌ๋ฆฌ - Logback
```
๐ก ๋ก๊น(logging) : ์ ํ๋ฆฌ์ผ์ด์์ด ๋์ํ๋ ๋์ ์์คํ์ ์ํ๋ ๋์ ์ ๋ณด๋ฅผ ์๊ฐ์์ผ๋ก ๊ธฐ๋กํ๋ ๊ฒ
```

<br>


์๋ฐ๋ฅผ ์ฌ์ฉํ๋ฉด์ ๊ฐ์ฅ ๋ง์ด ์ฌ์ฉ๋๋ ๋ก๊น ํ๋ ์์ํฌ๋ Logback์ผ๋ก `Logback`์ log4j ์ดํ์ ์ถ์๋ ๋ก๊น ํ๋ ์์ํฌ๋ก slf4j๋ฅผ ๊ธฐ๋ฐ์ผ๋ก ๊ตฌํ๋์๊ณ , log4j๋ณด๋ค ์ฑ๋ฅ์ด ์ข๋ค. <br> ๋ํ spring-boot-start-web ๋ผ์ด๋ธ๋ฌ๋ฆฌ ๋ด๋ถ์ ๋ด์ฅ๋์ด ์์ด ๋ณ๋ ์์กด์ฑ์ ์ถ๊ฐํ์ง ์์๋ ๋๋ค.

<br>


Logback์ ์ฌ์ฉํ๊ธฐ ์ํด์๋ ๋ฆฌ์์ค ํด๋ ์์ logback-spring.xml ํ์ผ์ ์์ฑํฉ๋๋ค.


#### logback-spring.xml ์ดํด๋ณด๊ธฐ

**Appender ์์ญ**
```๋ก๊ทธ์ ํํ๋ฅผ ์ค์ ํ๊ณ  ์ด๋ค ๋ฐฉ๋ฒ์ผ๋ก ์ถ๋ ฅํ ์ง ์ค์ ํ๋ ๊ณณ```
* ConoleAppender : ์ฝ์์ ๋ก๊ทธ ์ถ๋ ฅ
* FileAppender : ํ์ผ์ ๋ก๊ทธ ์ ์ฅ
* RollingFileAppender : ์ฌ๋ฌ ๊ฐ์ ํ์ผ์ ์ํํ๋ฉด์ ๋ก๊ทธ ์ ์ฅ
* SMTPAppender : ๋ฉ์ผ๋ก ๋ก๊ทธ ์ ์ก
* DBAppender : ๋ฐ์ดํฐ๋ฒ ์ด์ค์ ๋ก๊ทธ ์ ์ฅ

```xml
<appender name="console" class="ch.qos.logback.core.ConsoleAppender">
    <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
        <level>INFO</level>
    </filter>
    <encoder>                
        <pattern>[%d{yyyy-MM-dd HH:mm:ss.SSS}] [%-5level] [%thread] %logger %msg%n</pattern>
    </encoder>
</appender>

<appender name="INFO_LOG" class="ch.qos.logback.core.rolling.RollingFileAppender">
    <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
        <level>INFO</level>
    </filter>
    <file>${LOG_PATH}/info.log</file>
    <append>true</append>
    <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
        <fileNamePattern>${LOG_PATH}/info_${type}.%d{yyyy-MM-dd}.gz</fileNamePattern>
        <maxHistory>30</maxHistory>
    </rollingPolicy>
    <encoder>
        <pattern>[%d{yyyy-MM-dd HH:mm:ss.SSS}] [%-5level] [%thread] %logger %msg%n</pattern>
    </encoder>
</appender>
```

* `<filter></filter>` : ๊ฐ Appender๊ฐ ์ด๋ค ๋ ๋ฒจ๋ก ๋ก๊ทธ๋ฅผ ๊ธฐ๋กํ๋์ง ์ง์ ํ๋ค. <br>
* `<encoder></encoder>` : ๋ก๊ทธ์ ํํ ํ์์ ํจํด(pattern)์ผ๋ก ์ ์ํ๋ค.

<br>

ํจํด ์์)

```
<pattern>[%d{yyyy-MM-dd HH:mm:ss.SSS}] [%-5level] [%thread] %logger %msg%n</pattern>
```

* `%d` : ๋ก๊ทธ ๊ธฐ๋ก ์๊ฐ
* `%-5level` : ๋ก๊ทธ ๋ ๋ฒจ, -5๋ ์ถ๋ ฅ ๊ณ ์ ํญ์ ๊ฐ
* `%Logger{length}` : ๋ก๊ฑฐ์ ์ด๋ฆ
* `%thread` : ํ์ฌ ์ค๋ ๋๋ช
* `%msg(%message)` : ๋ก๊ทธ ๋ฉ์์ง
* `%n` : ์ค๋ฐ๊ฟ

<br>


**Root ์์ญ**

์ค์  ํ์ผ์ ์ ์๋ Appender๋ฅผ ํ์ฉํ๋ ค๋ฉด Root ์์ญ์์ Appender๋ฅผ ์ฐธ์กฐํด์ ๋ก๊น ๋ ๋ฒจ์ ์ค์ ํ๋ค.

```xml
<root level="INFO">
    <appender-ref ref="console"/>
    <appender-ref ref="INFO_LOG"/>
</root>
```


<br>


**Logback ์ ์ฉํ๊ธฐ**

Logback์ ์ถ๋ ฅํ  ๋ฉ์์ง๋ฅผ Appender์๊ฒ ์ ๋ฌํ  Logger ๊ฐ์ฒด๋ฅผ ๊ฐ ํด๋์ค์ ์ ์ํด์ ์ฌ์ฉํ๋ค.

<br>


* Logger ์ ์ธ
```java
private final Logger LOGGER = LoggerFactory.getLogger(ApiController.class);
Logger.info("Logback Test");
```

<br>


๊ฒฐ๊ณผ๋ก ์ฝ์ ํ๋ฉด์ ๋ก๊ทธ๊ฐ ์ถ๋ ฅ๋๋ค.

![แแณแแณแแตแซแแฃแบ 2023-01-10 แแฉแแฅแซ 12 48 11](https://user-images.githubusercontent.com/72512101/211349274-208540c1-2de5-4a4e-9798-87de8b9cccf9.png)




<br>


**์ฐธ๊ณ **

๐ https://developer.mozilla.org/ko/docs/Glossary/REST

๐ https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80

๐ https://dorothy-koo.gitbooks.io/springboot/content/chapter1.html
