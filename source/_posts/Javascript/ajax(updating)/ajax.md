---
title: Ajax & XMLHttpRequest
date: 
tags: javascript
---

# 비동기식 처리 모델

> - 동기적 처리 모델 : 순차적으로 태스크 실행, 어떤 작업이 수행 중이면 다음 작업을 무조건 대기
> - 비동기적 처리 모델 : 병렬적으로 태스크 실행, 태스크가 종료되지 않은 상태더라도 다른 태스크가 대기하지 않고 중간에 즉시 수행 (DOM이벤트, Timer함수..)

## 1. Ajax (Asynchronous JavaScript and XML)

- 자바스크립트를 이용해서 **비동기적(Asynchronous)**으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식
- 페이지 전체를 로드,렌더링 하지 않아도 페이지의 일부만 로드하여 갱신한다 => 빠르다, 부드러운 화면표시효과
  ![ajax](https://poiemaweb.com/img/ajax-webpage-lifecycle.png)

## 2. JSON (JavaScript Object Natation)

- 클라이언트와 서버 간데이터 교환을 위한 규칙 (데이터 포맷)
  - **순수한 텍스트로 구성**된 규칙이 있는 데이터 구조
- 일반 텍스트 포맷보다 효관적인 데이터 구조화 가능 (객체 리터럴과 비슷)
- XML포맷보다 가볍고 사용하기 간편하며 가동성도 좋다.

```js
    {
        "name" : "song",
        "gender" : "female",
        "hasDog" : false
    }

    // 키는 반드시 큰따옴표! (작은따옴표 사용불가!)

```

### 1.1 JSON.strigify

- 객체를 JSON형식의 **문자열로 변환**

```js
var obj = {
  name: "song",
  gender: "female"
};

var strObj = JSON.strigify(o);

console.log(typeof strObj, strObj);
// String {"name":"song", "gender":"female"}
```

### 1.2 JSON.parse

- JSON데이터를 가진 문자열을 **객체로 변환** (역직렬화 (Deserializing))

```js
var obj = JSON.parse(strObj);

console.log(typeof obj, obj);
// Object {name:'song', gender: 'female'}
```

## 2. XMLHttpRequest

- 브라우저는 XMLHttpRequest객체를 이용해 Ajax요청(비동기적)을 생성하고 전송할 수 있다. (통신)

### 2.1 Json Server 설치

- json파일을 사용하여 간단한 시뮬레이션을 위한 REST APO Mock Server를 구축할 수 있는 툴

> 1. `npm i -g json-server`
> 2. **db.json** 파일 생성된다. (데이터베이스 역할)