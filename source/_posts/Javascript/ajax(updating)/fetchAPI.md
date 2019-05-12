---
title: Fetch API
date: 2019-05-10 16:17:20
tags:
  - javascript
  - 네트워크통신
---

> **API** (application Programming Interface)
>
> - 프로그램이 동작하는 환경을 제어하기 위해서 환경에서 제공되는 조작 장치
> - 프로그래밍 언어를 통해 조작 할 수 있다.
> - **다른 서버로부터 데이터를 손쉽게 가져올 수 있게 하는 수단**

<br/>
> - 동기 : 요청사항이 완료될 때까지 다른 것을 실행하지 않는다.
> - 비동기 : 다른 것을 실행하면서 요청사항을 기다린다.
<br/>
# fetch API : 비동기적 처리 방식

- `XMLHttpRequest` API를 더욱 유연하고, 분명하게 손쉽게 사용할 수 있다.

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

### 1. **fetch('a')**

- 웹브라우저가 <u>'a'라는 파일을 **서버에게 요청**하는 메소드</u>, 데이터를 얻을 수 있게 해준다.

### 2. **.then(실행할 코드)**

- 서버가 응답하는 과정이 모두 **끝나면** <u>'실행할 코드(함수)'가 실행</u> 된다.

> fetch는 비동기적이기 때문에 fetch가 응답이 끝나지 않았더라도 다른 js기능들은 상관없이 실행되게 됨.
> => **서버로부터 응답받는 과정이 끝날 때 알아서 then메서드가 실행됨**

### 3. **response 객체**

- <u>웹서버가 응답한 **결과**를 갖고있는 객체</u>, 웹브라우저와 서버의 **통신상태**를 알 수 있다.

- response 객체의 status 속성 (**_response.staus_**)
  1. 200 : 파일 갖고오기 성공
  2. 404 : 파일없음

### 4. **.catch(실행할 코드)**

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

---

## API 예 )

### Geolocation API

- 사용자의 위치정보를 얻을 수 있다.
- 사용자의 권한이 필요하다.

- **navigator.geolocation** 객체 : .geolocation 객체를 통해 지오로케이션서비스를 사용할 수 있다.

1. .getCurrentPosition() : 사용자의 현재 위치를 알 수 있다.
   - 사용자의 현재 위치를 탐지하는 비동기적 요청
   - 파라미터는 기복적인것과 추가로 2가지를 선택적으로 입력할 수 있다.
     1. **첫번째 파라미터** : 위치 탐지 성공 시 정의된 콜백함수 실행
     2. 두번째 파라미터 : 위치 탐지 에러가 생길 경우 정의된 콜백함수 실행
     3. 세번째 파라미터 : 옵션 객체
        - 위치값이 반환된 최대 시간과 요청을 대기할 시간, 그리고 높은 정확도를 사용할 지 여부를 지정

```js
navigator.geolocation.getCurrentPosition(
  function(geoSucess) {},
  function(geoErr) {}
);
```

2. Coordinates.Position 객체 : 사용자의 위치는 position객체의 프로퍼티를 갖는다.
   - .coords : 현재 위치를 정의하는 객체(Coordinates 객체)
   - position 객체
     - .coords.latitude : 위도 (소수점으로 표현)
     - .coords.longitude : 경도 (소수점으로 표현)
     - altitude,accuracy ...

```js
navigator.geolocation.getCurrentPosition(geoSuccess, geoErr);

function geoSuccess(position) {
  console.log(position.coords.latitude);
  console.log(position.coords.longitude);
}

function geoErr() {
  console.log("err");
}
```
