---
title: Javascript Prototype
date: 2019-04-21 16:07:12
tags: javascript
---

# Prototype

> 1. Parent를 통해 만들어질 Child객체들에게 **정보를 전달**해주는 <u>연결에 대한 속성</u> (prototype property)
> 2. Child객체를 만든 <u>Parent객체와 연결된 링크</u>를 알려주는 역할(prototype link)

`프로토타입 => 자바스크립트가 **객체지향언어**라는 것에 중요한 역할`

> `_proto_` : 자신이 물려받은 prototype 속성

<br>

### 1. 상속 : 부모객체가 갖고 있는 속성(변수, 메소드)등을 물려받아 새로운 객체를 만들 수 있다.

1. 자식 객체

- 부모 객체의 속성을 물려받을 수 있다.
- 자식 객체는 자신만의 새로운 속성을 갖을 수 있다.

`자바스크립트의 모든 객체는 자신의 부모 역할을 담당하는 객체와 prototype을 통해 연결되어 있다!`

`모든 함수의 최상위 객체는 Object이다!!`

```js
// Person이라는 생성자 생성
function Person(name) {
  this.name = name;
}

// prototype : 생성자함수가 갖고 있는 기본적인 특수 속성(property) - > 상속받기 위한 수단(부모와 자식을 이어주는 연결다리)
// Person생성자의 prototype속성에 새로운 속성(name,introdce)을 만들어준다.

Person.prototype.name = null;
Person.prototype.introduce = function() {
  return "My name is" + this.name;
};

// Programmer라는 생성자 생성
function Programmer(name) {
  this.name = name;
}

// Programmer.prototype에  new Person을 통해  Person 생성자의 속성을 상속받는다!
Programmer.prototype = new Person();

// Programmer.property에 coding 메소드를 추가
Programmer.prototype.coding = function() {
  return "hello world";
};

// p1은 new Programmer를 통해 Programmer생성자 속성을 상속받는다!
var p1 = new Programmer("song");

document.write(p1.introduce());
// Person > Programmer > p1 인 형태이기 때문에 p1은 Person의 속성을 물려받아 p1.introdce()값을 나타낼 수 있다.
```

> 생성자 new : 생성자함수를 갖게 된다.
> 생성자의 역할 : 생성자함수의 프로퍼티를 갖게 해준다.

<br>

## 2. prototyoe Chain

```js
function Grand() {}

Grand.prototype.exist = true;

function Parent() {}

Parent.prototype = new Grand();

function Child() {}

Child.prototype = new Parent();

var song = new Child();

console.log(song.exist);
```

#### 1. prototype chain 과정

- child -> parent -> grand -> Object

1. 객체 **song**에서 <u>프로퍼티 exist</u>를 찾는다.

2. 없다면 , new Child를 통해 부모가 Child라는 것을 알아낸다.

   - 이제, **부모의 속성을 상속받아 부모의 prototype에 접근**할 수 있다.

3. Child.prototype.exist를 찾는다.

4. 없다면, new Parent를 통해 부모가 Parent라는 것을 알아낸다.

   - 이제, 부모의 속성을 상속받아 부모의 prototype에 접근할 수 있다.

5. Parent.prototype.exist를 찾는다.

6. 없다면, new Grand를 통해 부모가 Grand라는 것을 알아낸다.

   - 이제, 부모의 속성을 상속받아 부모의 prototype에 접근할 수 있다.

7. Grand.prototyoe.exist를 찾는다.

- <u>Grand.prototype.exist = true</u> 이므로 **_true_**값을 내뱉는다.
- 생성자 함수로 생성된 객체의 프로토타입 체인
  !(프로토타입 체인){https://poiemaweb.com/img/constructor_function_prototype_chaining.png}
