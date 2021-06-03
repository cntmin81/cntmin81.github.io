---
title: "엘라스틱서치(Elasticsearch)와 키바나(Kibana) 설치"
date: 2021-06-03 15:36:00 +0900
categories: ELK study
---

### 설치순서
1. JDK설치
2. 엘라스틱서치(Elasticsearch)설치
3. 키바나(Kibana)설치

### 1.JDK설치
맥 터미널에서 java를 실행 설치 되어있지 않다면 Java가 없다는 창이 뜬다.
더 많은 정보를 누르면 oracle홈페이지로 이동. JDK를 다운 받아서 설치하면 된다.
#### 설치 확인
터미널에서 java -version을 실행한다.

### 2.엘라스틱서치(Elasticsearch)설치
1. https://www.elastic.co/kr/downloads/elasticsearch
2. 환경에 맞는 파일을 다운로드
3. 압축해제
4. /bin/elasticsearch

### 3.키바나(Kibana)설치
1. https://www.elastic.co/kr/downloads/kibana
2. 환경에 맞는 파일을 다운로드
3. 압축해제

### 실행방법
#### 엘라스틱서치(Elasticsearch)
```bash
# 압축푼 디렉토리에서
$ /bin/elasticsearch
```

#### 키바나(Kibana)
1. config/kibana.yml파일을 에디터에서 연다.
2. elasticsearch.hosts가 엘라스틱서치를 볼 수 있게 지정한다. (엘라스틱서치에서 변경한게 없다면 기본값OK)
3. 아래 커맨드 실행
```bash
# 압축푼 디렉토리에서
$ /bin/kibana
```
키바나(Kibana)실행전에 엘라스틱서치(Elasticsearch)가 기동되어 있어야 한다.
