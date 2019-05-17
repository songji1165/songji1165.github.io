---
title: Ajax & XMLHttpRequest
date: 2019-05-10 16:07:10
tags:
  - javascript
  - 네트워크통신
---

# 비동기식 처리 모델과 Ajax

> 1. 동기적 처리 모델 : 순차적으로 태스크 실행, 어떤 작업이 수행 중이면 다음 작업을 무조건 대기
> 2. 비동기적 처리 모델 : 병렬적으로 태스크 실행, 태스크가 종료되지 않은 상태더라도 다른 태스크가 대기하지 않고 중간에 즉시 수행 (DOM이벤트, Timer함수..)
>    <br>

## 1. Ajax (Asynchronous JavaScript and XML)

1. 자바스크립트를 이용해서 비동기적으로 서버와 브라우저가 데이터를 주고 받는 방식
   <br>
2. **서버와 통신**하기 위해 `XMLHttpRequest` API를 사용
   <br>
3. 페이지 전체를 로드하지 않아도 **페이지의 일부만 로드**하여 갱신한다 => 빠르다, 부드러운 화면표시효과
   <img src="https://poiemaweb.com/img/ajax-webpage-lifecycle.png" width="400px%">

      <!-- ![ajax](https://poiemaweb.com/img/ajax-webpage-lifecycle.png){: width="400px" height=""} -->

      <br/>

## 2. XMLHttpRequest 객체

- **통신**
  1.  브라우저는 *XMLHttpRequest객체*를 이용해 **Ajax요청(비동기적)**을 생성하고 전송
  2.  서버에게서 받은 응답을 *XMLHttpRequest객체*가 처리

```js
// 1. XMLHttpRequest 객체 생성
var xhr = new XMLHttpRequest();

// 2. 비동기식 방식으로 requet 오픈
xhr.open("GET", "/users");

// 3. 서버와의 통신이 끝났을 때 호출되는 이벤트
//response가 클라이언트에 도달하면 함수 호출
xhr.onreadystatechange = function(e) {
  //XMLHttpRequest.readyState 프로퍼티가 변경(이벤트 발생)될 때마다 콜백함수(이벤트 핸들러)를 호출
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

// 4. Requeset 전송 : data인자로 전송할 데이터 전달
xhr.send(data);
```

1. `XMLHttpRequest.open ( method, url)`

   1. 서버 요청 준비
   2. `<form method = "METHOD" action = "URL">` 과 같다.
   3. **method** : HTTP 방식 (GET, POST, PUT, DELETE)
   4. **url** : 요청 보낼 URL - url정보는 METHOD의 단어가 들어가면 안 된다!
      <br>

2. `XMLHttpRequest.onreadystatechange`

   - 서버에 응답에 대한 처리, 이벤트 핸들러 (서버의 응답처리 단계마다 이벤트핸들러가 호출 됨) 1. `XMLHttpRequest.readyState` : 응답 상태의 값 - 0 (uninitialized) : request가 초기화되지 않음 - 1 (loading) : 서버와의 연결 성사됨 - 2 (loading) : 서버가 request를 받음 - 3 (interactive) : request(요청)을 처리하는 중 - 4 (DONE) : request에 대한 처리가 끝났으며 응답할 준비가 완료됨
     <br> 2. `XMLHttpRequest.status` : 응답 상태 코드 - 200 : 응답 완료 - 404 : NOt Found
     <br> 3. `XMLHttpRequest.DONE` : (4) request에 대한 처리가 끝났으며 응답할 준비가 완료됨
     <br> 4. `XMLHttpRequest.responseText` : 서버의 응답을 텍스트 문자열로 반환
     <br>

3. `XMLHttpRequest.send`
   1. 메소드의 인자로 전송할 데이터를 서버에 전달
   2. GET : 쿼리문자열로 데이버를 서버에 전송
   3. POST : Request Body에 담아 서버에 전송
      <br>
4. 예외 처리 : 통신 에러 상황일 때
   1. `onreadystatechange`메서드에서 예외에러를 발생시키게 된다.
   2. `if .. then`구문을 `try .. catch`로 바꾼다.

```js
try {
  if (xhr.readyState === 4 && xhr.status === 200) {
    console.log(xhr.responseText);
  } else {
    console.log("err");
  }
} catch (err) {
  alert("cauch Exception", err.description);
}
```

## <br>

---

<br>

> **jQuery Ajax**
>
> ```js
> $("button").click(function() {
>   $.ajax({
>     url: "./time3.php",
>     dataType: "json",
>     success: function(data) {
>       var str = "";
>       for (var name in data) {
>         str += "<li>" + data[name] + "</li>";
>       }
>       $("div").html("<ul>" + str + "</ul>");
>     }
>   });
> });
> ```
