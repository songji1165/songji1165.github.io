---
title: Javascript Promise (es6)
date: 2019-05-20 16:07:12
tags: javascript
---

# Promise ( ES6 )

> <mark>비동기 처리를 동기적으로 처리할 수 있게 한다!</mark>

<br>

### 1. 비동기 처리의 예

1. **setTimeout**
2. **addEventLitener**
3. **XMLHttpRequest**

```js
console.log("1");
setTimeout(function() {
  console.log("2");
}, 0);
console.log("3");
```

`콘솔 창에는 1 , 3 , 2 가 찍힌다!`

##### => 비동기 처리의 실행 순서를 제어하기 위해 <u>콜백함수 중첩</u> 실행

```js
function hell(callback) {
  setTimeout(function() {
    callback();
  }, 1000);
}

hell(function() {
  console.log("1");

  hell(function() {
    console.log("2");

    hell(function() {
      console.log("3");
    });
  });
});

// 1 , 2 , 3
```

`콜백 헬 : 콜백함수를 여러개 중첩하면 작업 내용 이해가 어려움! 에러시 예외 처리가 어려움!`

---

## 2. Promise

- 콜백 헬를 해결할 수 있다!
- <mark>비동기 처리를 동기적으로 처리하기 위한 라이브러리</mark>
  - Promise에서 비동기 처리를 실행하고, 그 처리가 끝난 후 다음 처리를 실행할 수 있게 한다!(resolve, reject)

#### 1. Promise 객체 생성

`var promise = new Promise( resolve, reject ) { ... }`

- Promise를 종료시키는 콜백함수
  1. resolve : 함수 안의 처리가 성공적으로 끝났을 때 호출되는 콜백함수
  2. reject : 함수 안의 처리가 실패했을 때 호출되는 콜백함수

#### 2. resolve 함수 + then 메서드

- resolve 함수의 인수 값은 then 메서드에 인수로 전달되어 처리한다.

#### 3. reject 함수 + catch 메서드

- reject 함수의 인수 값은 catch 메서드에 인수로 전달되어 처리한다.

```js
var promise = new Promise(resolve, reject){
  setTimeout(function(){
    var num = parseInt(prompt("5미만의 숫자 입력"))

    if(num <= 5){
      resolve(num)
    } else {
      reject(`숫자 ${num}은 오류입니다. 5미만으로 입력해주세요.`)
    }
  }, 1000)
}

promise
.then(
  funtion(num){
    console.log(num)
})
.catch({
  function(err){
    console.log(err)
  }
})
```

> **catch** 메서드 대신 **.then에 두번째 인자**로 사용할 수 있다!

<br>

#### 4. Promise의 콜백함수에 새로운 인수 넣기

```js
// money에 다양한 인자를 넣을 수 있다!!

function buy(money) {
  return new Promise(function(res, rej) {
    var pay = parseInt(prompt("지불할 금액"));
    var balance = money - pay;

    if (balance > 0) {
      res(balance);
    } else {
      rej(`잔액은 ${money}입니다. 구매할 수 없습니다.`);
    }
  });
}

buy(500)
  .then(function(balance) {
    console.log(`잔액은 ${balance}입니다.`);
  })
  .catch(function(err) {
    console.log(err);
  });
```

<br>

#### 5. Promise.all 메서드

- Primise.all 안의 **모든 비동기 처리가 성공적으로 끝나야** Promise가 종료되고 **다음 작업**이 이루어진다!
- `Promise.all([Array])`
  1. **resolve** : Array의 value가 담긴 **response 배열**을 받음
  2. **reject** : **가장 먼저 실패한** reject 함수의 인수를 받음

```js
Promise.all([
  new Promise(resolve => setTimeout(() => resolve(1), 3000)),
  new Promise(resolve => setTimeout(() => resolve(2), 2000)),
  new Promise(resolve => setTimeout(() => resolve(3), 1000))
])
  .then(console.log) // 3초 뒤에 resolved [ 1, 2, 3 ]
  .catch(console.log);
```

<mark>3초 뒤에 resolved [ 1, 2, 3 ]</mark>

<br>

#### 6. Promise.race 메서드

- **가장 먼저 종료**한 Promise 객체의 결과만 반환
- `Promise.race([Array])`
  1. **resolve** : **가장 먼저 종료된** value만 받음
  2. **reject** : **가장 먼저 실패한** reject 함수의 인수를 받음

```js
Promise.race([
  new Promise(resolve => setTimeout(() => resolve(1), 3000)),
  new Promise(resolve => setTimeout(() => resolve(2), 2000)),
  new Promise(resolve => setTimeout(() => resolve(3), 1000))
])
  .then(console.log) // 1초 뒤에 resolved  3
  .catch(console.log);
```

<mark>1초 뒤에 resolved 3</mark>
