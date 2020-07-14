---
title: API
date: 2019-05-15 16:17:20
tags:
  - javascript
---

# API (application Programming Interface)

> - 프로그램이 동작하는 환경을 제어하기 위해서 환경에서 제공되는 조작 장치
> - 프로그래밍 언어를 통해 조작 할 수 있다.
> - **다른 서버로부터 데이터를 손쉽게 가져올 수 있게 하는 수단**

## - API 예

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
