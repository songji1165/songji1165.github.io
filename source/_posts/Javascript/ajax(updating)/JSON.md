---
title: JSON
date: 2019-05-10 16:07:12
tags:
  - javascript
  - 네트워크통신
---

# JSON (JavaScript Object Natation)

1. 클라이언트와 서버간 데이터 교환을 위한 규칙 (**데이터 포맷**)
   - **순수한 텍스트로 구성**된 규칙이 있는 데이터 구조
        - 텍스트로 이루어져있어 사람, 기계 모두 읽고 쓰기 쉽다.
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

- 객체를 **JSON형식의 문자열로 변환**

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
