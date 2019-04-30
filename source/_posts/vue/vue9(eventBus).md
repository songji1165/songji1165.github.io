---
title: 9. Vue eventBus
date: 2019-04-26 16:07:12
tags: Vue
---

# EventBus

- 형제 컴포넌트간 데이터 공유
- 형제 컴포넌트를 이어주는 가상의 부모컴포넌트 역할 (이벤트 신호 받고 이벤트 신호로 받은 데이터 사용)

### 1. 이벤트버스 생성 (**main.js**)

```js
export const eventBus = new Vue();
```

### 2. 이벤트 발생 (컴포넌트 .vue 파일)

```js
    import {eventBus} from '파일경로'

    ...

    eventBus.$emit('sendEvent','helloWorld')
    // sendEvent라는 이름으로 신호 보냄
```

### 3. 이벤트 구독 (컴포넌트 .vue 파일)

```js
import {eventBus} from '파일경로'

...

eventBus.$on("sendEvent", function(text) {
  console.log(text);
});
// $on == v-on과 같은 이벤트리스너
// sendEvent라는 데이터를 받아서 사용


eventBus.$on("sendEvent", text => {
  this.editText = text;
});
//콜백함수(return) : 애로우함수로 사용해야 this가 vue모델을 가리킴
```
