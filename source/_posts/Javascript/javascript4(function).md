---
title: 자바스크립트 함수 Function
date: 2019-04-14 16:07:12
tags: javascript
---

# 함수 function

> 1. 어떠한 작업을 실행하기 위해 그룹화한 것
> 2. 함수를 쓰는 이유
>    - 코드의 재사용
>    - 코드의 그룹화, 모듈화 -> 가독성, 유지보수 또한 좋음
>      <br>

## 1. 함수 선언문

#### 1. 함수 선언식 : <u>함수명</u>을 써야 한다.

    ```js
        function name () {
            name() //자기자신을 호출할 수 있다.(재귀함수)
        }
    ```

<br>
#### 2. 함수 표현식 ( 함수리터럴 ) : 다른 방법으로 함수를 표현한다.
- **변수**에 함수를 넣음

    ```js
        var foo = function () { // 익명함수 :함수명이 없는 것
            console.log('함수리터럴')
        }
    ```

<br>
#### 3. Function 생산자 함수 (잘 사용하지 않음!)
<br>
# 2. 자바스크립트 함수는 객체이다. ***일급객체***!

> 일급객체
>
> - 생성, 대입, 연산, 인자 또는 반환값으로서의 전달 등 <u>프로그래밍언어의 기본적 조작을 제한없이 사용</u>할 수 있는 대상
>   <br>

#### 1. **일급객체** 특징

1. <u>함수리터럴</u>로 표현이 가능하다.
2. <u>변수나 자료구조(객체, 배열 등)에 저장</u>할 수 있다.
3. 함수의 <u>매개변수(Parameter)</u>에 전달할 수 있다.
4. <u>반환값(**return**)</u>으로 사용할 수 있다.

```js
// 1. 무명의 리터럴로 표현이 가능하다.

// 2. 변수나 자료구조에 함수를 저장할 수 있다.

var foo = function() {
  console.log("변수안에 함수 담았다.");
};

var obj = {
  foo: function() {
    console.log("메서드 : 객체 안에 담긴 함수.");
  }
};

// 3. 함수를 매개변수로 전달할 수 있다.

var foo2 = function(para) {
  // para : 매개변수
  return console.log(para);
}; // 1

foo2(1); // foo2는 1이라는 인수(argument)를 통해 1이라는 값을 매개변수(Parameter)로 받게 된다.

// 4. return으로 사용할 수 있다.

var foo3 = function() {
  return 1 + 1;
}; // 2
```

> 1. 파라미터는 <u>3개 이하</u>가 좋다!
> 2. **_Return_** : 함수는 return을 만나면 함수 밖으로 값을 내보낸다!
>
> - <u>함수에서 받아낸 값을 다시 사용해야하는 경우 return을 사용!!!</u>

<br>

## 3. 매개변수(Parameter, 인자) vs 인수(Argument)

#### 1. 매개변수(Paramenter)

1. 함수에게 추가적인 정보가 필요할 경우 매개변수 사용
2. 인수(Argument)를 담는 **변수**
   - 함수 내에서 <u>변수와 동일하게 메모리 공간을 확보</u>
   - <u>전달받은 인수(Argument)는 매개변수에 할당</u>

 <br>

#### 2. 인수(Argument)

- 함수에서 넘겨받는 실제 값

```js
var foo = function(p1, p2) {
  console.log(p1, p2);
};

foo(1);

// 1 undefined
```

> 인수를 전달받지 못한 매개변수 : 값이 할당 되지않은 **undefined**가 됨
> <br>

## 4. 인수 (Argument) vs Rest Parameter (ES6)

#### 1. 인수(Argument)는 **_유사배열_**이다

- **유사배열 객체**(Array-like Object) : 일반 객체에 **length**라는 프로퍼티를 가진 객체
- 하지만, <u>배열은 아니다</u> => .push()같은 배열 메소드는 사용할 수 없다!

```js
function foo() {
  var result = 0;

  for (var i = 0; i < arguments.length; i += 1) {
    result += argumnets[i];
  }
  // argument가 유사배열이기 때문에 .length와 arguments[i]를 사용할 수 있다.
}

foo(1, 2, 3, 4, 5);
// Arguments(5) [1, 2, 3, 4, 5]
```

<br>
#### 2. ES6 : Rest Parameter **_(...rest)_**

- **argument보다 사용하기 편리**하다
- 유사배열이 아닌 **진짜 배열**로 넣어준다!
- **Spread연산자( ... )을 사용**

```js
function foo(...rest) {
  // rest대신 다른 이름이여도 된다.

  return console.log(rest);
} // [1,2,3,4,5]

foo(1, 2, 3, 4, 5);

function foo(num1, num2, ...rest) {
  // num1,2 또한 다른 이름이어도 된다.
  console.log(num1); // 1
  console.log(num2); // 2
  console.log(reset.length); // 5
}
```
