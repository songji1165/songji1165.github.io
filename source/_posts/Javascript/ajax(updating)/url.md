---
title: URL 구조 분석
date: 2019-06-02 16:07:12
tags:
  - javascript
  - 네트워크통신
---

`생활코딩 참고`

# url 구조

<br>

#### 실제 URL : http://opentutorials.org:3000/main?id=HTML&page=12

`프로토콜 :// 웹서버 : 서버주소 / 파일이름 ? 쿼리`

<br>

### 1. `http`

- **프로토콜 통신규칙** : 웹브라우저와 웹서버과 데이터를 주고받기 위한 통신 규칙

### 2. `opentutorials.org`

- **host(domain)** : 특정한 인터넷에 연결되어 있는 컴퓨터를 가르키는 주소

### 3. `3000`

- **port** : 서버의 주소
- 기본 port : 80 (기본 port값 생략 가능)

### 4. `main`

- **path** : 컴퓨터 안의 어떤 디렉토리의 어떤 파일을 나타냄

### 5. `?id=HTML&page=12`

- **qeury string** : 웹서버에게 읽고싶은 데이터의 정보를 전달하는 역할
