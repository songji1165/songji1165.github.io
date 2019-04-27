---
title: Vue Router 사용하기
date:
tags: Vue
---

# Vue-router 사용하기

- Vue라우터는 Vue.js에서 제공하는 컴포넌트
  - 기본 컴포넌트 사용은 `import Vue from 'vue'` 기본!!
- 라우터에 컴포넌트 매핑 후, 어디에 렌더링할지만 작성하면 된다!

#### Vue라우터 컴포넌트

1. `<router-view></router-view>` : 현재 라우터에 맞는 컴포넌트 렌더링, 요청 url에 따라 컴포넌트 렌더링
2. `<router-link to=""></router-link>`
   1. vue-router에서 제공하는 컴포넌트
   2. 주로 **_네비게이션_**을 위한 컴포넌트
   3. <u>a태그</u> 대신 `<router-link>`로 **링크**를 건다.
   4. `to` prop은 경우에 따라 v-bind `:to`로도 사용한다.
   5. 장점 1. 히스토리모드와 해시모드에서 모두 <u>동일한 방식</u>으로 작동하기 때문에 #를 붙이거나 삭제할 필요없다. 2. 히스토리 모드에서, 클릭 이벤트를 차단하여 페이지 로드를 막아준다. (**prventDefalt()**와 같은 기능)
      <br/>

## 1. Vue-router 설치

1. `npm i vue-router --save`
2. Vue router를 사용하기 위해서 **import작업이 필요**
   - 최상단 **main.js**에 import 시켜준다.

```js
// vue-router라이브러리를 가져온다.
import VueRouter from "vue-router";

// vue-router라이브러리를 사용기 위해 미들웨어 작업을 해준다.
Vue.use(VueRouter);
```

<br/>

### 2. 싱글 페이지 앱

```js
//main.js
...

// 1. 라우터 컴포넌트 정의
const Login = { template : `<div>Login Page</div>`}
const NotFoud = { template : `<div>Page Not Found</div>`}


// 2. 라우터 정의
// 각 라우터는 반드시 컴포넌트와 매핑되어야 한다!
const routes = [
    {path : '/', component:App},
    {path : '/login', component:Login},
    {path : '*', component:NotFound},
]


// 3. 'routes' 옵션과 함께 router 인스턴스 만들기
const router = new VueRouter({
    routes : routes
})


// 4. 루트 인스턴스를 만들고 라우트 전달
new Vue({
    el: "#app",

  router, //라우터 속성 전달

  render: h => h({
    template: `<router-view></router-view>`
  }) //html대신 렌더 함수를 통해 라우터 컴포넌트 렌더링
})
})

```

<br/>
### 3. 라우터 객체를 별도 파일로 분리

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

import router from "./router"; // index.js 자동 연결

new Vue({
  el: "#app",
  router,
  render: h =>
    h({
      template: `<router-view></router-view>`
    })
});
```

### 4. 라우트 컴포넌트 파일 분리!! (작업이 많아 질수 있기 때문에 파일 분류를 잘하자!)

- components 폴더 : 컴포넌트 정의 파일
- router 폴더 : 라우터 정의 파일

1. src에 폴더 만들기 'components' => 폴더 안에 'Home.vue','Login.vue', 'NotFound.vue' 파일 만들기
2. *index.js*에 라우트 컴포넌트 삭제, 수정
   - 라우팅에 관한 로직만 담겨진다.

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

3. _main.js_ 수정

```js
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

<br/>
### 5. 라우터 링크를 사용하여 비동기적 페이지 만들기

- `<router-link>`는 주로 네이게이션에서 주로 사용 된다!

1. components 폴더에 _'Navbar.vue'_ 파일 만들기
   - 네비게이션 컴포넌트 생성

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
