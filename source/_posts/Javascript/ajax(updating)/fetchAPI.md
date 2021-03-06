---
title: Fetch API
date: 2019-05-10 16:17:20
tags:
  - javascript
  - 네트워크통신
---

# fetch API : 비동기적 처리 방식

> **API** (application Programming Interface)
>
> - 프로그램이 동작하는 환경을 제어하기 위해서 환경에서 제공되는 조작 장치
> - 프로그래밍 언어를 통해 조작 할 수 있다.
> - **다른 서버로부터 데이터를 손쉽게 가져올 수 있게 하는 수단**

<br/>

`동기 : 요청사항이 완료될 때까지 다른 것을 실행하지 않는다.`
`비동기 : 다른 것을 실행하면서 요청사항을 기다린다.`

<br/>

## 1. **fetch('a')**

1. 웹브라우저가 <u>'a'라는 파일을 **서버에게 요청**하는 메소드</u>, 데이터를 얻을 수 있게 해준다.
2. `XMLHttpRequest` API를 더욱 유연하고, 분명하게 손쉽게 사용할 수 있다.

```js
 <input type="button"
    value="fetch"
    onclick="
        fetch('파일이름').then(function(response){

            response.text()
                  .then(function(data){

                // 모든 작없이 끝난 후 함수 안에 코드가 작동함
                // data 변수 안에 서버가 응답한 데이터가 들어있다.

                    document.querySelector('article').innerHTML = data
                })
        })
    ">

```

<br>

## 2. **.then(실행할 코드)**

- 서버가 응답하는 과정이 모두 **끝나면** <u>'실행할 코드(함수)'가 실행</u> 된다.

`fetch는 비동기적이기 때문에 fetch가 응답이 끝나지 않았더라도 다른 js기능들은 상관없이 실행되게 됨.`
**`=> 서버로부터 응답받는 과정이 끝날 때 알아서 then메서드가 실행됨`**

<br>

## 3. **response 객체**

1. <u>웹서버가 응답한 **결과**를 갖고있는 객체</u>, 웹브라우저와 서버의 **통신상태**를 알 수 있다.

2. response 객체의 **status** 속성 (**_response.staus_**)
   1. 200 : 파일 갖고오기 성공
   2. 404 : 파일없음

<br>

## 4. **.catch(실행할 코드)**

- **err**일 경우 실행할 코드가 실행됨

```js
fetch("html")
  .then(function(response) {
    return response.json;
    //response : respose의 네트워크정보만 알 수 있다.(ex. status ...)
    //response.json()을 통해 응답받은 데이터 즉, json파일의 데이터를 갖고옴
  })
  .then(function(data) {
    //위의 then에서 json파일이 준비가 완료되면, 두번째 then으로 넘어온다.
    // data 인자에는 response.json 데이터가 담겨 있다.

    console.log(data);
    //json 데이터를 console에 출력해준다.
  })
  .catch(function(err) {
    console.log(err);
    //에러가 생기면 에러사항을 console에 출력해줌
  });
```
