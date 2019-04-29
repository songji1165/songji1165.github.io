---
title: 자바스크립트 Scope
date: 2019-04-22 16:07:12
tags: javascript
---

# 스코프 Scope

- 스코프 : javascrip의 유효범위

## 1. 전역스코프, 지역스코프

- 전역 스코프 ( 전역변수 , 전역함수 ) (Global) : 자바스크립트 어디에서나 사용 가능
- 지역 스코프 ( 지역변수 , 지역함수 ) (Local) : <u>함수 코드 블록이 만든 스코프 영역에서만</u> 사용 가능

```js
function outerFunction() {
  var inner = "var"; // 지역 변수

  function innerFuction() {
    // 지역 함수
    코드;
  }
} //  outerFunction 함수 안에서 선언된 변수, 함수 : 지역변수, 지역함수

outerFunction();
// outerFunction이 호출됨으로써 스코프 안의 지역 변수, 함수도 호출됨!

innerFunction();
// 스코프 안의 지역변수, 지역함수는 그 안에서만 존재!!!
// innerFunction을 호출하지 못함
```

## 2. 스코프체인

- 프로토타입 체인과 같은 방식 : 아래에서 위로 찾아 나간다.

```js
var value = "global";

function outFunc() {
  // 이때의 value는 local영역의 value가 없기 때문에 global 의 value 를 참조합니다.
  console.log(value);

  function innerFunc() {
    // 이때도 마찬가지로 local에 value가 없기 때문에 global 의 value 를 참조합니다.
    console.log(value);
    // innerValue 라는 지역 변수 선언합니다.
    var innerValue = "local";
  }
  innerFunc();
}
outFunc();
// error: innerValue is not defined
// 외부에서 내부 스코프의 값을 참조할 수 없습니다. global 에서는 innerValue가 선언된 줄도 모르고 있습니다.
console.log(innerValue);
//(3)

function outter() {
  console.log(value);
  // (2)

  function inner() {
    console.log(value);
    // (1)

    var innerValue = "local";
    //inner함수 안에서만 참조 가능
  }
}

outter();

console.log(innerValue);
// error : 지역변수는 스코프안에 갇혀 있기 때문에 참조 할 수 없다
```

- (1) inner안에 value가 없기 때문에 위의 스코프 단위의 value를 찾는다.
- (2) outter안에 value가 없기 때문에 global영역의 value값을 가져오게 된다.
- (3) 전역변수 var value = **"global"** 의 값을 내뱉는다.

> console.dir(변수,함수 명)
> : `[[Scope]]`에서 글로벌변수나 글로벌함수를 찾을 수 있다.
