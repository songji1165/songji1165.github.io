---
title: 13. Vue Router 기본 컴포넌트
date: 2019-04-28 17:07:12
tags: Vue
---

# Vue 라우터 컴포넌트

## 1. router-view Props

- `<router-view> </router-view>`
- 현재 라우터에 맞는 컴포넌트를 렌더링 해준다.
  요청 url에 따라 컴포넌트 렌더링

## 2. router-link

1. `<router-link to=""></router-link>`
2. 주로 **_네비게이션_**을 위한 컴포넌트
   - <u>a태그</u> 대신 `<router-link>`로 **링크**를 건다.
3. **to** prop: 링크 지정
   - 경우에 따라 v-bind `:to`로도 사용한다.
4. 장점
   - 히스토리모드와 해시모드에서 모두 <u>동일한 방식</u>으로 작동하기 때문에 #를 붙이거나 삭제할 필요없다.
   - 히스토리 모드에서, 클릭 이벤트를 차단하여 페이지 로드를 막아준다. (**prventDefalt()**와 같은 기능)

## 3. 라우터 링크를 사용하여 비동기적 페이지 만들기

1. components 폴더에 _'Navbar.vue'_ 파일 만들기

```js
<template>
  <div>
    <router-link to="/">Home</router-link>
    <router-link to="/login">login</router-link>
  </div>
</template>
```

2. _app.vue_ 파일 수정

```js
    <template>
        <div id="app">
            <Navbar></Navbar> // 컴포넌트 사용
            <router-view></router-view> // 라우터에 따라 해당 데이터로 변경 됨
        </div>
    </template>

    <script>
        // 네비게이션 컴포넌트 import 시켜줌
        import Navbar from './components/Navbar'


        export default {
        name: 'app',
        components : { Navbar }, //컴포넌트 추가
        data () {
            return {
            }
        }
    </script>
```
