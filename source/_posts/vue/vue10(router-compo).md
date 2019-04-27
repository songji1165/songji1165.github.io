---
title: Vue Router 관리하기
date:
tags: Vue
---

# 라우터 효율적으로 관리하기

## 1. 라우터 객체를 별도 파일로 분리

- src에 폴더 만들기 'router' => 폴더 안에 'index.js' 만들기

```js
// index.js

import Vue from "vue";
import VueRouter from "vue-router";
import App from "../App.vue";

Vue.use(VueRouter);

const Login = {
  template: `<div>Login Page </div>`
};
const NotFound = {
  template: `<div>Page not found</div>`
};

const routes = [
  { path: "/login", component: Login },
  { path: "*", component: NotFound }
];

const router = new VueRouter({
  mode: "history",
  // 브라우저에서 라우팅할 때 실행모드 #
  // 브라우저에 history API가 있을 때 #없이 쓸 수 있다.
  // mode를 history로 바꿔줌 (크롬에서 가능)

  routes: routes
});

export default router;
// router를 내보낸다
```

```js
// main.js

import Vue from "vue";

import router from "./router"; // index.js 생략가능, 자동 연결

new Vue({
  el: "#app",
  router,
  render: h =>
    h({
      template: `<router-view></router-view>`
    })
});
```

## 2. 라우트 컴포넌트 파일 분리

- src에 폴더 만들기 'components' => 폴더 안에 'Home.vue','Login.vue', 'NotFound.vue' 파일 만들기

```js
import Vue from "vue";
import VueRouter from "vue-router";
import Home from "../components/Home.vue";
import Login from "../components/Login.vue";
import NotFound from "../components/NotFound.vue";

Vue.use(VueRouter);

const routes = [
  { path: "/", component: Home },
  { path: "/login", component: Login },
  { path: "*", component: NotFound }
];

const router = new VueRouter({
  mode: "history",
  routes: routes
});

export default router;
```

```js
// main.js 수정

import Vue from "vue";
import router from "./router";

import App from "./App.vue";
//루트컴포넌트 App.vue 연결!

new Vue({
  el: "#app",
  router, //라우터 설정
  render: h => h(App)
  // 루트컴포넌트 App에 렌더링한다.
});
```
