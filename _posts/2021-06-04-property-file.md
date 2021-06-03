---
title: "프로퍼티파일 사용하기"
date: 2021-06-04 06:03:00 +0900
categories: spring study
---

### 사용자 정의 프로퍼티 파일
```
#datasource.properties
guru.username=user
guru.password=0000
guru.jdbcurl=test.db
```

```java
// datasource.properties설정
@PropertySource("classpath:datasource.properties")
@Configuration
public class GreetingServiceConfig {

    
    @Bean
    FakeDataSource fakeDataSource(
                                  // Value어노테이션으로 할당 가능
                                  @Value("${guru.username}") String username,
                                  @Value("${guru.password}") String password,
                                  @Value("${guru.jdbcurl}")String jdbcurl) {
        FakeDataSource fakeDataSource = new FakeDataSource();
        fakeDataSource.setUsername(username);
        fakeDataSource.setPassword(password);
        fakeDataSource.setJdbcurl(jdbcurl);
        return fakeDataSource;
    }
```

### 스프링부트 기본 제공 프로퍼티(application.properties)
```
# application.properties
spring.profiles.active=cat,EN
guru.username=Shin
guru.password=0000
guru.jdbcurl=test.db
```

```java
// datasource.properties설정이 필요없다!!
// @PropertySource("classpath:datasource.properties")
@Configuration
public class GreetingServiceConfig {

    
    @Bean
    FakeDataSource fakeDataSource(
                                  // Value어노테이션으로 할당 가능
                                  @Value("${guru.username}") String username,
                                  @Value("${guru.password}") String password,
                                  @Value("${guru.jdbcurl}")String jdbcurl) {
        FakeDataSource fakeDataSource = new FakeDataSource();
        fakeDataSource.setUsername(username);
        fakeDataSource.setPassword(password);
        fakeDataSource.setJdbcurl(jdbcurl);
        return fakeDataSource;
    }
```

### 환경별 프로퍼티 파일
```
# Dev환경. 파일명의 '-'이후에 환경이름을 써줌 
# application-dev.properties
guru.username=DevDBUser
guru.password=DevPassword
guru.jdbcurl=DevDBUrl
```
```
# QA환경. 파일명의 '-'이후에 환경이름을 써줌 
# application-qa.properties
guru.username=QaDBUser
guru.password=QaPassword
guru.jdbcurl=QaDBUrl
```
```
# application.properties파일
# 여기서 환경으 지정해준다
spring.profiles.active=qa
```
