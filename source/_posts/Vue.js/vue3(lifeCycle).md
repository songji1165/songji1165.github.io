---
title: 3. Vue Life Cycle
date: 2019-04-10 16:35:12
tags: Vue
---

# Vue 인스턴스 라이프 싸이클

1. Vue 객체가 생성될 때 초기화 작업을 수행

   > 1. 데이터관찰
   > 2. 템플릿 컴파일
   > 3. DOM에 객체 연결
   > 4. 데이터 변경시 DOM 업데이트

2. 모든 라이프사이클 훅은 _자동으로 this 컨텍스트를 인스턴스에 바인딩_
   => **화살표함수로 라이프사이클 정의하면 안됨**!!
   `created : () => this.fetchTodos()`

## 옵션 / 라이프사이클 훅

![lifecycle](https://kr.vuejs.org/images/lifecycle.png)

## beforeCreate -> created -> _created_ -> beforeMount -> _mounted_ -> beforeUpdate -> _Updated_ -> beforeDestroy -> destroyd

- 타입 : Function
- Vue 인스턴스 생성에서 가장 먼저 호출 (window.onload와 비슷하다!)
- `$el`
    : Vue 인스턴스가 관리하는 루트 DOM엘리먼트

```js
new Vue({
  el: "#app",

  beforeCreate() {
    // 인스턴스 초기화 직후 최초 호출
    // 데이터와 이벤트 등 설정 전
  },

  created() {
    // 인스턴스가 작성된 후 동기적으로 호출
    // 데이터 이벤트 초기화 후
    // vitual DOM은 생성 전 ($el 접근 X)
  },

  beforeMount() {
    // 여기부터 컴포넌트 접근 가능
    // vitual DOM 생성 중 ($el 접근 X)
  },

  mounted() {
    // $el포함, 모든 컴포넌트에 접근 가능
    // 제일 많이 사용!!!!!!!!
  },

  beforeUpdate() {
    // 컴포넌트 마운트 된 후, 데이터 변경 감지  =>  렌더링 전에 실행
    // 이 단계에서는 컴포넌트의 새로운 state에 접근할 수 있다.
  },

  updated () {
      // beforeUpdate와 반대
      // 렌더링 후에 호출
      // 렌더링 후 접근할 경우가 있을시 updated 사용!
  },

});
```
### 2. created, mounted, updated
1. created : $el 데이터 접근 전
2. mounted : $el 데이터 포함, 모든 컴포넌트 접근 가능
3. updated : DOM렌더링 후 데이터 변경 감지 시 리렌더링

> fetchdata 등을 사용할 떄 라이프주기를 잘 생각해서 사용하자!
> - ***mounted*** 많이 사용!!