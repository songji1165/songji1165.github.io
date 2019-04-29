---
title: 자바스크립트 Closure
date: 2019-04-24 16:07:12
tags: javascript
---

# 클로저 Closure

- 함수형 프로그래밍 언어에서 사용되는 중요한 특성

- 클로저 :
  - 내부함수가 자신을 포함하고 있는 <u>외부함수의 스코프에 접근할 수 있는 것</u>
  - 종료된 외부함수임에도 외부함수로 인해서 파생된 이미 사라진 외부함수에 접근하여 값을 갖고 올 수 있다.
  - 함수가 선언 됬을 때의 **렉시컬환경**을 기억한다.

```js
function outter() {
  var title = "외부함수 지역변수";

  return function() {
    alert(title);
  };
}

var inner = outter();
// 변수 inner에 의해서 outter 함수는 호출 되고 실행되어져서 자신의 역할을 끝냈다. 그리고 그 안의 지역변수 title은 소멸됬다.
// 이 부분에서의 outter를 설명하는 것
// 새로 outter() 하면,  다시  호출 /실행 / 지역변수 발생 / 소멸이 된다.

inner();
// inner안의 함수 호출, return값 호출
// title의 값은 outter안의 지역변수이다.
// <클로져> 외부함수 outter에 접근하여 title값을 가져온다.
```

> 내부함수가 외부함수의 지역변수에 접근 할 수 있다.
> **외부함수**는 외부함수의 지역변수를 사용하는 내부함수가 소멸 될 때까지 소멸되지 않는다!

> - 렉시컬 스코핑(Lexical scoping)
>   스코프가 결정되는 범위를 말하며, `함수, 변수를 호출할 때가 아니라 함수, 변수를 어디에 선언하였는지에 따라 결정되는 것`
> - 렉시컬 환경(Lexical environment)
>   함수가 선언됬을 때의 스코프
>   **클로저** : 함수가 생성될 때의 렉시컬환경을 기억하는 것

### 스코프체인과 렉시컬 스코프의 관계

```js
function outerFunc() {
  var inner = "local";

  function innerFunc() {
    console.log(inner);
    // 변수 inner는 값이 없기 때문에 그 위에 함수에서 지역변수 inner값을 찾게 된다.
  }

  innerFunc();
}

outerFunc();
// local
```

- innerFunc가 상위 스코프에 접근할 수 있는 것은 렉시컬스코프의 레퍼런스를 차례대로 저장하고 있기 때문이다.
  > 렉시컬의 저장 값 덕분에 함수 안의 함수, 그 함수 안의 함수 등이 되어도 꼬이지 않고 잘 실행되는 것 !!!

## 클로저를 사용하는 이유

1. 비밀변수 (Private variable)
   - Javascript는 비밀 변수가 없다 => function scope를 이용해서 비밀 변수를 만들어 줄 수 있다.
   - 비밀변수 : 외부에서는 함수 안의 지역변수를 사용할 수 없다.

```js
function foo() {
  var a = 10; // 비밀변수

  return function(b) {
    a = b;
  };
}
```

```js
function outter(title) {
  return {
    get: function() {
      return title;
    },
    set: function(_title) {
      title = _title;
    }
  };
}

var outFunc = outter("a");
var outFunc2 = outter("b");

outFunc.get(); // a
outFun2.get(); // b

outFunc.set("비밀변수값 변경");

outFunc.get(); // 비밀변수값 변경
outFun2.get(); // b
```

> 파라미터로 값을 받은 변수title은 outFunc.set메소드 뿐이다!
> 객체 내무에서만 사용해야하는 값이 노출됬을 때 오류를 줄일 수 있다.

2. 함수 지연 평가

- 실행 값을 하나하나 끝까지 확인해보는 것이 아니라 실행 중에 조건이 맞는 것이 있다면 그 부분에서 종료된다.
- return : 함수는 return을 만나면 return값을 내뱉고 종료한다.

```js
function add(a) {
  return function(b) {
    return a + b;
  };
}

var add10 = add(10);
// 파라미터 a=10이 된다.

var result = add10(10);
// add10(10) : return 함수의 파라미터 b=10
// a=10 , b=10
// 그 결과, result = 20
```

3. 커링

- 함수 하나가 n개의 인자를 받는 과정을 n개의 함수로 각각의 인자를 받도록 하는 것 (this 대신 사용할 수 있다.)
- 클로저를 이용해서 각 외부함수로 접근 할수 있기 때문에 각 변수값을 기억하고 사용할 수 있다.

```js
function foo(a) {
  return function(b) {
    return function(c) {
      console.log(a + b + c);
    };
  };
}

foo(10)(20)(30);
```
