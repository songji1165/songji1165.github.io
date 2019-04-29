---
title: Vue의 기본 기능 1
date: 2019-04-09 16:07:12
tags: Vue
---

> Vue 기본기능

1. 선언적렌더링
2. 조건문과 반복문
3. 사용자 입력 핸들링
4. 컴포넌트

<br/>

## 1. 선언적 렌더링(1) : 텍스트보간법 (데이터바인딩), v-bind (attribute 바인딩)

#### 1. **텍스트보간법**

- **_데이터 바인딩_**의 기본 형태이다.

```text
    <p id="ex">{{message}}</p>
```

```js
new Vue({
  el: "#ex",
  data: {
    message: "데이터렌더링한다(el로 연동 후 data에 텍스트보간법으로 렌더링)"
  }
});
```

```text
    hi
```

> 데이터와 DOM이 연결되어 모든 것이 **반응형**으로 작동한다.

- **el** : HTML**엘리멘트ID**로 바인딩

- **data** : 데이터와 함수가 담기는 공간
  - <u>data에 있는 속성들</u>은 화면에 렌더링 될때 **_반응형_**으로 나타난다.
  - data 객체의 있는 것들은 프록시 처리 된다.
    - 프록시 : 클라이언트와 서버 사이에서 중계한다고 생각하면 된다. (반응형)
      data를 거치고 나면 data 안의 속성들이 클란이언트 측으로 보여진다.

#### 2. **v-bind** (attribute 바인딩)

```text
    <p id="ex" v-bind:title="message">마우스를 올리세요</p>
```

```js
new Vue({
  el: "#ex",
  data: {
    message: "v-bind:title title속성을 데이터렌더링한다 hover시 title"
  }
});
```

> title속성은 message값과 바인드하여 `<p title="message">`로 수정된다.

- **v-bind:속성 = "a"** : a라는 값을 받아 html 속성을 수정
- 약어 **:속성 = "a"**

1. v-bind **클래스 바인딩**

   - <u>active클래스</u> 존재여부는 <u>isActive</u>의 **참 속성(true)**에 의해 결정된다.
     ```text
         <div v-bind:class="{active:isActive}">
     ```
     ```js
     data: {
       isActive: true;
     }
     ```

2. v-bind **인라인스타일 바인딩**

   1. :style="{font-size:fontSize+'px', color:activeColor}"
      data : {
      fontSize : 10,
      activeColor : 'red'
      }

   2. :style="styleObject"
      data : {
      styleObject : {
      fontSize: '10px',
      color: 'red',
      }
      }

## 2. 조건문과 반복문 : v-if, v-for

#### 1. 조건부 블록 : **v-if** 디렉티브

- v-if 값이 **[TRUE - 보임][false - 안 보임]**

```text
    <div id="ex">
        <p v-if="seen">{{message}}</p>
        <button @click="clickSeen">클릭</button>
    </div>
```

```js
new Vue({
  el: "#ex",
  data: {
    message: "v-on을 통한 클릭메서드 만들기(복수니까 methods)",
    seen: true
  },
  methods: {
    clickSeen: function() {
      this.seen = !this.seen;
    }
  }
});
```

> **v-else, v-else-if**도 가능하다.

    단, <u>v-if 바로 뒤</u>에 있어야 기능이 가능하다.

#### 2. 반복문 블록 : **v-for** 디렉티브

- v-for 블록 안에는 부모 범위 속성에 대한 모든 권한이 부여된다.

- **<u>item in items</u>** 형태의 특별한 문법이 필요

```text
    <ul id="iter">
        <li v-for="i in items">{{i.text}}</li>
    </ul>
```

```js
    new Vue = ({
        el : "#iter",
        data : {
            items : [
                {text : 1},
                {text : 2},
                {text : 3}
            ]
        }
    })
```

- 현재 항목의 **index**를 부여할 수 있다. **<u>(i,index) in items</u>**

```text
    <ul id="iter">
        <li v-for="(i,index) in items">
            {{parentText}} - {{index}} - {{i.text}}
        </li>
    </ul>
```

```js
    new Vue({
        el : "#iter",
        data : {
            patentText : '부모 범위 속성 모든 권한',
            items = [
                {text : js},
                {text : vue}
            ]
        }
    })
```

## 3. 사용자 입력 핸들링 : v-model, v-on

#### 1. **v-model** 디렉티브

- 폼입력 바인딩
- 양방향 데이터 바인딩을 생성
- input type : text , textarea, checkbox, radio, select ...

```text
    <div id="bind">
        <input type="text" v-model="message">
        <p> {{message}} </p>
    </div>
```

```js
    new Vue({
        el : "#bind",
        data : {
            message = ""
            }
        }
    })
```

#### 2. **v-on** 디렉티브

- v-on은 이벤트핸들링
- **'v-on:이벤트'** 전달인자 뒤에 <u>이벤트값</u>이 들어간다.
  - 약어 : **@clcik=""**

```text
    <p id="ex" v-on:click="handleClick">클릭하세요{{message}}</p>
```

```js
new Vue({
  el: "#ex",
  data: {
    message: ""
  },
  methods: {
    hadleClick: function() {
      this.message = "클릭했다";
    }
  }
});
```

---

> 1. **디렉티브 : v-**

- <u>'v-' 접두사</u>가 있는 특수 속성
- 디렉티브 속성 값은 단일 javajs 표현식이다. (**v-for 제외**)

2. **전달인자(:)** : 일부 디렉트브는 전달인자(:)를 사용할 수 있다.
