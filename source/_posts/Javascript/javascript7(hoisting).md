# 호이스팅 Hoisting

- hoisting : 끌어올리다 (자바스크립트 엔진의 기능)
- 함수나 변수 선언문을 어디에 쓰더라도 실행 단계에서 Scope 맨 위로 끌어올린다. => 어디선든 순서 상관없이 호출 가능
- 변수호이스팅 , 함수호이스팅

1. 변수 호이스팅

```js
// 변수의 생성단계는 호이스팅과 관련이 있다.

// 선언단계 & 초기화단계
var a;

// 할당단계
a = 1;
```

```js
console.log(foo);
// undefined

var foo = 12;

console.log(foo);
// 12
```

- 변수는 선언 & 초기화, 할당단계로 나뉘어졌있다.
- **변수의 호이스팅은 변수 선언문**을 호이스팅한다.
- 값이 할당 되기 전에 변수를 호출하면
  => 저장공간은 참조되고 있지만 **값이 없다** : **<u>undefined</u>가 출력**되는 것

2. 함수 호이스팅

- 함수 선언식, 함수 표현식, function 생성자 함수 중 **_함수선언식_**만 호이스팅 된다.
  - 함수 표현식은 변수 호이스팅이 적용되어 erro가 발생
- 함수는 선언되면 함수 전체가 호이스팅 된다.

```js
sum(1, 3); // 4

// 함수 선언식
function sum(num1, num2) {
  return console.log(num1 + num2);
}

result(3); // Uncaught TypeError: result is not a function

// 함수 표현식 (var result 는 빈 값을 먼저 참조하고 있다 undefined)
var result = function(num) {
  return console.log(num);
};
```

===

> 호이스팅으로 인해 오류가 날 수 있다!
> 함수나 변수는 항상 먼저 선언해 두도록 하자!
