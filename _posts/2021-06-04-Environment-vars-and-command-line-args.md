---
title: "환경변수와 커맨드라인 파라미터"
date: 2021-06-04 05:54:00 +0900
categories: spring study
---
스프링부트에서느 환경변수와 커맨드라인 파라미터로 프로퍼티파일의 내용을 덮어쓰기가 된다.

### 환경변수
```bash
#guru.username=username을 usernameFromEnv로 덮어쓴다
GURU_USERNAME=usernameFromEnv
```

### 커맨드라인 파라미터
```bash
#GURU_USERNAME=usernameFromEnv를 다시 덮어쓴다.
--guru.username=usernameFromArg
```
