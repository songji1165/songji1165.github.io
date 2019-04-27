---
title: Vue Router 라이브러리 사용하기
date:
tags: Vue
---

# Vue-router 사용하기

- Vue라우터는 Vue.js에서 제공하는 컴포넌트

  - 기본 컴포넌트 사용은 `import Vue from 'vue'` 기본!!

- 라우터에 컴포넌트 매핑 후, 어디에 렌더링할지만 작성하면 된다!

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

1. 라우터 컴포넌트 정의

   - `const RouteCompo = { template :`..`}`
   - 컴포넌트 파일 생성해서 export, import

2. 라우터 정의

   - path 경로에 따라 각 컴포넌트 매핑
   - `const routes = [ { path: '/' , component : RouteCompo }]`

3. 라우터 인스턴스 생성

   - `const router = new VueRouter({ routes })`

4. 라우터 컴포넌트 렌더링
   - `new Vue({ router , render()})`
   - Vue 인스턴스에 router속성 전달 , 렌더함수를 통해 렌더링

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
    routes
      // routes : routes 와 동일
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
### 3. 라우터 효율적으로 관리하기
1. 라우터 객체를 별도 파일로 분리 : src 하위 폴더 'router' 만들기! 
2. 라우트 컴포넌트 파일 분리 : src 하위 폴더 'components' 만들기!
