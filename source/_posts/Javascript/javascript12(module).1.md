---
title: 자바스크립트 Module Pattern
date: 2019-04-25 16:07:12
tags: javascript
---

# 모듈패턴 (Module Pattern)

- 변수가 섞일 수 있기 때문에 전역변수는 지양한다! => 지역변수로 만들자!

## 1. 네임 스페이스 (Name Space)

- 누구나 접근이 가능하다. **(Public)**

```js
var x = 5; //전역변수

// obj 네임스페이스
var obj = {
  x: "local",
  y: function() {
    console.log(this.x); // x = local
  }
};

console.log(x); // 5

console.log(obj.x); // local

obj.x = "global";

console.log(obj.x); // global
```

> 누구나 PUBLIC하게 접근이 가능하기 때문에 값을 맘대로 바꿀 수 있다!
> => 캡슐화로 해결

## 2. 캡슐화(Private)

- 클로저, 스코프를 이용하자
  - 외부 스코프는 내부 수코프에 접근하지 못한다.

```js
function phone() {
  // 변수 power : 지역 변수
  var power = "on";

  function checkPower() {
    console.log(power);
  }

  function playMusic() {
    console.log("노래 실행");
  }

  // return을 통해 밖에서 checkPower와 playMusic을 사용할 수 있다.
  return {
    checkPower: checkPower,
    playMusic: playMusic
  };
}

var iphone = phone(); //return 값

iphone.playMusic(); // '노래실행'
iphone.checkPower(); // on
```

> power라는 변수를 모르더라도 던져준 함수만으로 power의 값을 확인 할 수 있다!

#### 즉시실행함수

- phone의 기능들을 사용하기 위해 위의 코드와 같이 한번 return을 받은 후에 사용하는 단계를 **즉시 실행 함수**를 이용하면 줄일 수 있다!

```js
var pF = (function() {
  var x = "local";

  function getX() {
    console.log(x);
  }

  return {
    getX: getX
  };
})();

console.log(pF); // {getX : f}
```

```js
var phone = (function() {
  var power = "on";

  function checkPower() {
    console.log(power);
  }

  function playMusic() {
    console.log("노래 실행");
  }

  return {
    checkPower: checkPower,
    playMusic: playMusic
  };
})();

// var iphone = phone()
// 즉시실행함수 덕에 생략 가능

//바로 변수 phone으로 함수 실행
phone.playMusic(); // '노래실행'
phone.checkPower(); // on
```
