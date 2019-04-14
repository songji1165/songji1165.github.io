---
title: 자바스크립트 객체 Object 
date: 
tags: javascript
---

# 객체 Object
- 원시타입을 제외한 모든 것은 객체이다.
- **키(key)**와 **값(value)**로 구성된 속성(property)의 집합이다.
- 데이터를 한 곳에 **모으고 구조화**하는데 유용하다.

## 1. 객체의 속성(Property)과 메서드
1. 속성(property) : 데이터를 의미한다.
    - **key(속성명)**와 **value(속성값)**으로 표현
    - key는 중복선언시 이전에 있던  프로퍼티를 덮어쓴다.
2. 메서드(method) : 데이터를 참조하고 조작할 수 있는 동작을 의미한다.
    - 객체에 제한되어 있는 ***함수 프로퍼티***이다.
```js
    // 1. 프로퍼티
    var obj = {
        key1 : 'value1',
        key2 : 'value2',
        key1 : 'value3' 
    }
    console.log(obj.key1) // key1의 값은 value3이 된다. 

    // 2. 메서드
    var obj2 = {
        key : function () {
            console.log('객체의 값이 함수면 메서드이다.')
        }
    }
    obj2.key()
```

## 2. 객체 생성법
> 1. 리터럴방식 {}
  2. 생성자 함수(사용자 정의 함수) => **es6이전에 많이 사용 되었음**
  3. 생성자 new Object() => 비추

1. 리터럴방식
- 가장 일반적인 객체 생성 방식
- 가독성이 좋고, 오류발생이 적다.
```js
    var obj = {}; //빈 객체 생성
    obj.name = 'song';
    obj.age = '20';
    
    console.log(typeof obj); // Object
    console.log(obj) // {name:'song', age:'20'}
```

2. 생성자 함수 (사용자 정의 함수)
- 모듈화에 많이 쓰인다. => 프로퍼티가 동일한 여러개의 객체를 간평하게 생성할 수 있다!
    > 생성자 함수 특징
      1. 생성자 함수 이름은 ***대문자***로 시작 (생성자함수로 인식함)
      2. ***this*** : <u>this.(속성명 or 메서드명)</u>
        - 생성자 함수가 생성할 **인스턴스(자기자신)**를 가리킨다.
```js
    // name매개변수를 받는 Person 생성자 함수 생성 
    var Person = function(name,age){
        // this는 자기자신 즉, Person
        this.name = name;
        this._age = name; // _ : 외부로 노출이 안될 값
        this.say = function () {
            console.log('my name is' + this.name )
        }
    }

    var p = new Person('song', 20)
    p.say() // my name is song

```

3. 생성자 new Object
- 가독성이 떨어지고 인자로 원시적 타입등이 들어가는 경우 오류가 발생하기 쉽다. => 비추!!!!
```js
    var obj = new Object() // Object 선언
    console.log(obj.constructor === Object) // true
    // constroctor은 해당 Object가 어떤 상태인지 알려준다.

    obj.name = 'song'
    obj.age = 20
    
    console.log(obj) // {name: 'song', age: 20}
```
> ***constroctor***은 해당 Object가 어떤 상태인지 알려준다.

## 3. 객체 속성을 <u>추가, 갱신, 삭제, 탐색</u>
- 추가, 갱신, <u>삭제 **delete**</u>
```js 
    var obj = {};

    obj.name = "song"; // 객체 속성 추가
    obj.name = "eunji"; // 객체 속성 갱신
    console.log(obj) // Object{name : 'eunji'}

    delete obj.name; // 객체 속성 삭제 delete
    console.log(obj); // Object {}
```
- 탐색 
    1. 마침표 표기법 **obj.name**
    2. 대괄호 표기법 **obj['name']**
    3. for-in문 
    4. for-of문 <u>(ES6)</u>
    > for-in, for-of는 객체에 포함된 모든 프로퍼티에 대해 루프를 실행
      - 객체는 순서가 보장되지 않는다 -> **for in문 안쓰는 것이 좋다**
      - ES6에서 이 점을 보완하여 **for of문**이 나왔다.
      - for-in(<u>객체의 프로퍼티 순회</u>) , for-of(<u>배열의 요소를 순회</u>)

```js
    var person = {
        name : 'song',
        age : 20
    };
    var key ;
    for (key in person) {
        console.log(key+ ':' + person[key])
    }
    //name : song, age : 20

    for (const value of person) {
        console.log(value)
    }
    // song, 20
```