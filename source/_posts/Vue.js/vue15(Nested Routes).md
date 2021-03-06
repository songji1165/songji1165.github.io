---
title: 15. Vue 중첩된 라우트
date: 2019-04-29 16:07:12
tags: Vue
---

# Nested Routes (중첩된 라우트)

- 앱 UI는 여러 단계로 중첩된 컴포넌트로 이루어져 있다 (Children)
  ![nested](https://github.com/songji1165/songji1165.github.io/blob/build/source/_posts/vue/nesty.jpg?raw=true)

```js
//app.vue

<template>
  <div>
    <router-view />
  </div>
</template>

// router-view는 최상위 outlet
```

```js
//index.js

const User = {
  template: `<div>
      <h2> User {{ $route.param.id }} </h2>
      <router-view></router-view>
    </div>`
};
// router-view는 중첩 outlet으로 Children 옵션에 해당하는 것이 렌더링 된다.

const router = new VueRouter({
  routes: [
    {
      path: "/user/:id",
      component: User,
      children: [
        // 하위경로지정 user/:id/profile ..
        { path: "profile", component: UserProfile },
        { path: "posts", component: UserPosts }
      ]
    }
  ]
});
```

> `/`로 시작하는 중첩라우트는 **루트 경로로 취급**된다! => `/`없이 써야 한다.
