---
title: Javascript 연산자와 조건문, 반복문
date: 2019-04-08 16:17:12
tags: javascript
---

# 연산자와 조건문, 반복문

### 1. 연산자

##### 1. 사칙연산 (+-\*/%)

- % 나머지 : 2%1 = 0
  <br>

##### 2. 비교연산자

1. == (equal operator) : 데이터타입은 달라도 실질적 의미만 같으면 true
2. === (strict operator) : 데이터타입, 실질적의 모두 같아야 true
   <br>

##### 3. 크기 비교 연산자 (부등호 > < >= <=)

<br>
##### 4. and(&&) or(||)연산자
<br>
##### 5. NOT연산자 !
- true, false를 반대로 출력해줌 !, !!
<br>
##### 6. 증감연산자 (++ --)

1. i++ 후위증감연산자 : i이후 1을 더해 나감
2. ++i 전위증감연산자 : i+1을 해준 이후 1을 더해 나감
   <br>

##### 7. **<mark>false로 간주되는 값</mark>**

1. **''** : 빈 값
2. **undefined ,var a;(=undefined)**
3. **null**
4. **NaN** (Not a Number)
5. **0**
   <br>

### 2. 조건문

##### 1. if(**조건-boolean**){} : 만족하는 데이터가 여러개일 경우

- if(조건){true} else {false}
- if(){} else if {} else {} : 조건문을 좀더 풍부하게 사용할 수 있다.
  <br>

##### 2. switch(선택문) : 여러 경우의 값 중 일치하는 데이터를 찾아 그 해당하는 코드를 실행

```js
switch(){
    case 값1 : 코드값;
    break;
    case 값2 : 코드값;
    break;
    default: false
}
```

<br>
### 3. 반복문

##### 1. `while(조건){ 반복 실행할 코드}`

```js
var i = 0;

while (i < 10) {
  console.log(i);
  i = i + 1;
}
```

<br>
##### 2. `for( 초기화; 조건 검사; 증감코드; ){ 반복 실행할 코드 }`

- 초기화 -> 조건검사 -> 실행 -> 증감 과정
  **=>** while문보다 느리다!

```js
for (var i = 0; i < 10; i += 1) {
  console.log(i);
}
```

<br>
##### 3. `do{ 반복 실행할 코드 } while (조건)` 
- do가 무조건 한번 실행이 된후 조건에 따라 반복실행
