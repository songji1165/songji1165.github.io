---
title: Ajax & XMLHttpRequest
date: 2019-04-26 16:07:12
tags: javascript
---

# 비동기식 처리 모델과 Ajax

> - 동기적 처리 모델 : 순차적으로 태스크 실행, 어떤 작업이 수행 중이면 다음 작업을 무조건 대기
> - 비동기적 처리 모델 : 병렬적으로 태스크 실행, 태스크가 종료되지 않은 상태더라도 다른 태스크가 대기하지 않고 중간에 즉시 수행 (DOM이벤트, Timer함수..)

## 1. Ajax (Asynchronous JavaScript and XML)

1. 비동기 자바스크립트와 XML이다.
2. **서버와 통신**하기 위해 `XMLHttpRequest객체`를 사용
3. 페이지 전체를 로드하지 않아도 **페이지의 일부만 로드**하여 갱신한다 => 빠르다, 부드러운 화면표시효과
   ![ajax](https://poiemaweb.com/img/ajax-webpage-lifecycle.png)

   <br/>

## 2. JSON (JavaScript Object Natation)

1. 클라이언트와 서버간 데이터 교환을 위한 규칙 (**데이터 포맷**)
   - **순수한 텍스트로 구성**된 규칙이 있는 데이터 구조
2. 일반 텍스트 포맷보다 효관적인 데이터 구조화 가능 (객체 리터럴과 비슷)
3. XML포맷보다 가볍고 사용하기 간편하며 가독성도 좋다.

```js
    {
        "name" : "song",
        "gender" : "female",
        "hasDog" : false
    }

    // 키는 반드시 큰따옴표! (작은따옴표 사용불가!)
```

#### 2.1 JSON.strigify

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

#### 2.2 JSON.parse

- JSON데이터를 가진 문자열을 **객체로 변환** (역직렬화 (Deserializing))

```js
var obj = JSON.parse(strObj);

console.log(typeof obj, obj);
// Object {name:'song', gender: 'female'}
```

## 3. XMLHttpRequest 객체

- 통신
  1.  브라우저는 *XMLHttpRequest객체*를 이용해 **Ajax요청(비동기적)**을 생성하고 전송
  2.  서버에게서 받은 응답을 *XMLHttpRequest객체*가 처리

### 3.1 Ajax 요청 처리

```js
// 1. XMLHttpRequest 객체 생성
var xhr = new XMLHttpRequest();

// 2. 비동기식 방식으로 requet 오픈
xhr.open("GET", "/users");

// 3. Requeset 전송
xhr.send();
```

1. `XMLHttpRequest.open ( method, url)`

   - 서버 요청 준비
   - **method** : HTTP 방식 (GET, POST, PUT, DELETE)
     | Method | Action | |
     | :---- | :--------------: | :-----: |
     | GET | index / retrieve | 모든 / 특정 리소스를 조회 |
     | POST | create | 리소스를 생성 |
     | PUT | UPDATE | 리소스를 갱신 |
     | DELETE | DELETE | 리소스를 삭제 |
   - **url** : 요청 보낼 URL
   - async (생략가능) : 비동기 조작 여부 (기본값 : true 비동기)
     > url정보는 METHOD의 단어가 들어가면 안 된다!

2. `XMLHttpRequest.send`
   - 준비된 요청 서버에 전달
   - GET : 쿼리문자열로 데이버를 서버에 전송
   - POST : Request Body에 담아 서버에 전송

### 3.2 Ajax 응답 처리

```js
//XMLHttpRequest.readyState 프로퍼티가 변경(이벤트 발생)될 때마다 콜백함수(이벤트 핸들러)를 호출

xhr.onreadystatechange = function(e) {
  //response가 클라이언트에 도달하면 함수 호출

  if (xhr.readyState === XMLHttpRequest.DONE) {
    // xhr.readyState : 통신상태 반환

    if (xhr.status === 200) {
      // xhr.status === 200 : 서버응답 정상

      console.log(xhr.responseText);
      // xhr.responseText : 서버에서 전송한 데이터
    } else {
      console.log("Error");
    }
  }
};
```

1. `XMLHttpRequest.readyState`
   - reponse가 클라이언트에 도달했는지 추적할 수 있는 프로퍼티
   - | value |      state       |                                                               |
     | :---: | :--------------: | :-----------------------------------------------------------: |
     |   0   |      UNSENT      |            XMLHttpRequest.open() 메소드 호출 이전             |
     |   1   |      OPENED      |            XMLHttpRequest.open() 메소드 호출 완료             |
     |   2   | HEADERS_RECEIVED |            XMLHttpRequest.send() 메소드 호출 완료             |
     |   3   |     LOADING      | XMLHttpRequest.responseText() 메소드 완성 상태 : 서버 응답 중 |
     | **4** |     **DONE**     |                        서버 응답 완료                         |
