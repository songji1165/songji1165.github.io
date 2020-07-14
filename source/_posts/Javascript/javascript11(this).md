---
title: Javascript THIS
date: 2019-04-25 16:07:12
tags: javascript
---

# THIS

> 함수를 호출할 때, <u>함수가 어떻게 호출되었는지에 따라</u> **this**에 바인딩할 객체가 동적으로 결정된다.

`렉시컬스코프 : 함수를 선언할 때 함수의 스코프를 결정`

<br>

```js
function foo(number) {
  console.log(arguments);
  console.log(this);

  return number * number;
}

square(2);
```

![this](https://github.com/songji1165/songji1165.github.io/blob/build/source/_posts/Javascript/this.jpg?raw=true)
`자바스크립트 함수는 호출 될 떄, 매개변수로 전달되는 인자값 이외에, arguments객체와 this를 암묵적으로 전달 받는다.`
<br>

### 1. 함수 호출 패턴

- 전역함수 내부함수 모두 this는 **_window(전역객체)_**이다.

```js
function outFunc() {
  console.log(this);
  // this 무조건 window

  var inner = function() {
    console.log(this);
    // this는 무조건 window
  };

  inner();
}

outFunc();
```

<br>
### 2. 메소드 호출 패턴

- 함수가 객체의 프로퍼티 값이면 메소드로서 호출된다. **this**는 <u>해당 메소드를 호출한 객체이다</u>

```js
var person = {
  name: "song",
  getName: function() {
    console.log(this); // person
    console.log(this.name); //song

    function inner() {
      console.log(this); // window
      // inner는 단지, 내부함수이므로 this는 전역객체인 window를 가리킴
    }
    inner();
  }
};

person.getName();
```

<br>

### 3. 생성자 호출 패턴

- 생성자 함수 : 기존 함수에 new연산자를 붙여서 호출하면 해당 함수
- 생성자함수를 호출하면 this 바인딩이 메소드나 함수 호출때와 다르게 동작

```js
var Person = function(name) {
  this.name = name;
  // this는 자신 (Person)
};

Person.prototype.getName = function() {
  console.log(this.name);
  // Person.prototype이기 때문에 프로토타입 내에서도 this는 Person

  function inner() {
    console.log(this); // window (내부함수!!!)
  }
  inner();
};

var p = new Person("song");
p.getName();
```

<br>
### 4. apply / call / bind 호출

- this를 특정 객체에 명시적으로 바인딩할 수 있게 한다.
- Function.prototype객체의 메소드 : .apply, .call, .call
