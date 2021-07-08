# config-server
`http://localhost:8888` 을 통해 config 정보를 제공한다.

## maven 라이브러리 추가
### pom.xml
```xml
<dependencies>
   ...
   <!-- config-server 라이브러리 -->
   <dependency>
       <groupId>org.springframework.cloud</groupId>
       <artifactId>spring-cloud-config-server</artifactId>
   </dependency>
   <!-- basic 인증으로 http 보호 -->
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-security</artifactId>
   </dependency>
   <!-- http 서비스 -->
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-web</artifactId>
   </dependency>
   ...
</dependencies>
```

## config-server 설정
1. config-server 활성화 - `main()` 실행 클래스에서 `@EnableConfigServer` 설정
2. config-server 정보설정 - `application.yml` 에서 설정
    * `spring.cloud.config.server.git` 으로 git 저장소 정보 설정
    * `spring.security.user` 로 인증 계정정보 설정

### 주요 키워드
- @EnableConfigServer