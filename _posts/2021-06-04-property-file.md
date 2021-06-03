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

### 프로퍼티 파일 바인딩
```java
// SfgConfiguration.java
// Configuration, ConfigurationProperties로 바인딩할 프로퍼티를 지정
// POJO클래스에 바인딩 된다
@ConfigurationProperties("guru")
@Configuration
public class SfgConfiguration {
    private String username;
    private String password;
    private String jdbcurl;

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getJdbcurl() {
        return jdbcurl;
    }

    public void setJdbcurl(String jdbcurl) {
        this.jdbcurl = jdbcurl;
    }
}
```
```java
@Configuration
public class GreetingServiceConfig {
    // 아래와 같이 getter를 이용해 바인딩된 값을 가져올 수 있다.
    @Bean
    FakeDataSource fakeDataSource(SfgConfiguration sfgConfiguration) {
        FakeDataSource fakeDataSource = new FakeDataSource();
        fakeDataSource.setUsername(sfgConfiguration.getUsername());
        fakeDataSource.setPassword(sfgConfiguration.getPassword());
        fakeDataSource.setJdbcurl(sfgConfiguration.getJdbcurl());
        return fakeDataSource;
    }
```
