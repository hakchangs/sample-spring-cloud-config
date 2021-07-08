# Spring-Cloud-Configuration 샘플
`spring-cloud-config`는 설정정보를 통합관리하도록 도와준다.

## 구성
* `config-server`: 설정정보를 중앙관리 및 제공
  * Rest 서비스로 config 정보를 제공한다.
* `config-client`: config 정보를 사용하는 App
  * 일반적인 App으로 설정정보가 필요한 어떤 곳이든 `config-client`가 된다.
* `git-repository`: config 정보가 실제 저장될 저장소. `git`서버를 이용하여 저장하길 권고한다.
  * version 관리에 용이하므로 git 을 사용한다.

### config 정보제공 흐름

![spring-cloud-config](./doc-content/SpringCloudConfig.svg)

## 보안처리
...정리 필요...

## 실습(코드)

### 프로젝트 구조
```
root
ㄴconfig-server  //http://localhost:8888 을 통해 config 정보를 제공한다.
ㄴconfig-client  //http://localhost:8080 을 통해 rest 를 서비스한다. 이때, config 정보를 사용한다.
ㄴconfig-repo    //git-repository, properties 파일에 config 정보를 보관한다.
```

### 서비스별 구현사항
* [`config-server`](./config-server)
* [`config-client`](./config-client)
* [`config-repo`](./config-repo)

### 테스트
1. config-server 호출하기
```shell
$ curl http://root:s3cr3t@localhost:8888/config-client/development
```
2. config-client 호출하기
```shell
$ curl http://localhost:8080/whoami/some_username
```

## 참고
* https://www.baeldung.com/spring-cloud-configuration
* https://docs.spring.io/spring-cloud-config/docs/current/reference/html/
