---
title: 2. Vue 옵션
date: 2019-04-09 16:17:12
tags: Vue
---

# 1. Vue 옵션 (Data)

> - <u>화살표 함수 사용 금지</u> : this가 달라질 수 있기 때문
>   - 원래 vue인스턴스 안에서 사용하는 **this는 vue인스턴스**를 가리킴

## 1. data

1. 타입 : Object || Function
2. 반드시 **객체 형태**.

```js
//
new Vue({
  data: {}
});

// vue컴포넌트의 data는 모조건 함수!
Vue.component("compo", {
  data() {
    return {};
  }
});
```

## 2. computed / watch / methods

#### 1. computed (속성)

1. 타입 : Object `{key:Funtion}`
2. 복잡한 로직은 data대신 computed에서 처리
3. 계산된 속성으로 data변화시 다시 연산 됨
   - 캐싱(저장) => 데이터값이 변경될때만 재연산

```js
//{{message}}
//{{reversedMessage}}

new Vue({
  data: {
    message: "hello"
  },
  computed: {
    // message가 바뀔 때마다 연산됨

    reversedMessage: function() {
      return this.message
        .split("")
        .reverse()
        .join("");
    }
  }
});
```

#### 2. watch (감시자)

1. 타입 : Object `{key : String | Function | Object | Array }`
2. 키와 값(콜백)
3. 데이터 변화 감지 시 로직 수행 => 사용자가 만든 감시자(연산을 제어할 수 있음)

```js
// <input v-model="question">

new Vue({
  data: {
    question: ""
  },
  watch: {
    // input변경 될 때마다 수행

    question: function(newQ) {
      this.getAnswer();
    }
  },
  methods: {
    getAnswer() {}
  }
});
```

> Computed vs Watch
>
> - watch :데이터 호출과 같이 시간이 상대적으로 더 많이 소모되는 **비동기 처리에 적합**
> - 명령적인 watch 콜백보다는 계산된 속성 computed를 사용하는 것이 성능이 더 좋음

#### 3. methods

1. 타입 : Object `{ key : Function }`
2. Vue 인스턴스에 추가할 메소드

> 1. Computed vs Methods
>    - computed : data 속성에 변화가 있을 때만 다시 연산 (캐싱 => 필요시 재사용 )
>    - methods : 페이지 로드 시 호출 된 구간에서 연산 (캐싱 X => 매번 재 렌더링)
>    - 캐싱효과 필요시 computed 사용 권장!

## 2. props

1. 타입 : Object || Array
2. 부모한테 데이터를 받기 위함

```js
// 1. 기본
props : [ 'Message' ]

// 2. 타입 체크
props : { Message : String }

// 3. 타입 체크, 유효성 검사
props : {
  Message : {
    type : String,
    validator : function (value {
      return value >= 0
    }), ..
  }
}
```
