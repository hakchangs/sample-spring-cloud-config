# config-client
config 정보를 사용하는 주체. 일반적인 App 들이 config 를 사용할 수 있다.

여기서는 `http://localhost:8080` 을 통해 서비스를 제공한다.

`http://localhost:8080/whoami/{username}` 에서 config 정보를 조회하여 결과를 반환한다.

## config-server 연동설정
application.yml 에서 설정한다.
profile 과 configserver 정보를 통해 config 값을 가져온다.
```yaml
spring:
  application.name: config-client
  profiles.active: development
  config:
    import: configserver:http://localhost:8888
  cloud:
    config:
      uri: http://localhost:8888
      username: root
      password: s3cr3t

```

## config 정보 불러오기
```java
@Value("${user.role}")//일반적인 properties 불러오기와 규칙이 동일하다.
private String role;
```
