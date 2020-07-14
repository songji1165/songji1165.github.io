---
title: 15. Vue 환경변수
date: 2019-05-18 16:07:12
tags: Vue
---

# Vue 환경변수

> [Vue cli Environment Variables](https://cli.vuejs.org/guide/mode-and-env.html#using-env-variables-in-client-side-code)

`vue CLI3부터는 Vue dotenv가 내장되어있어 dotenv 패키지 설치가 필요 없다!`
<br>

#### 1. 프로젝트 루트 파일에 .env 파일 생성

- **`VUE_APP_`** 로 시작하는 변수 사용!

```text
// .env

VUE_APP_DB_USERNAME = song
VUE_APP_DB_PASSWORD = 1165
```

#### 2. <mark>.gitignore에 .env 추가</mark>

```js
// .gitignore
...

# local env files
.env.local
.env.*.local
.env    // .env 추가
```

#### 3. 환경변수 접근

```js
// index.js
...

const { VUE_APP_DB_USERNAME, VUE_APP_DB_PASSWORD } = process.env;
...

```
