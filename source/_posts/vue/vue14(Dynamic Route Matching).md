---
title: 14. Vue 동적 라우트 매칭
date: 2019-04-28 16:07:12
tags: Vue
---

# Dynamic Route Matching (동적 라우트 매칭)

- 주어진 패턴을 가진 라우트를 동일한 컴포넌트에 매핑해야하는 경우

```js
// 모든 사용자는 동일한 레이아웃을 가진다.
// 하지만 다른 사용자ID로 렌더링되어야 하는 User컴포넌트가 있을 수 있다.
// 이를, 동적 세그먼트로 해결!

const User = { template: `<div>User</div>` };

const router = new VueRouter({
  route: [{ path: "/user/:id", component: User }]
});
```

## 1. 동적 세그먼트

- `:id` (id는 변수라고 생각하자!) - `/user/song`와 `/user/lee`은 모두 같은 경로에 매핑된다.

1.  **_this.\$router_** : **router** 로 라우터에 관한 정보(API 레퍼런스)를 담고 있다.
    - <u>Vue.use</u>로 라우터를 주입해줌으로써 this.\$router로 접근 가능하다.
2.  **this.\$route** : 현재 활성화된 Route
    - `$route.params`, `$route.query`(url에 쿼리가 있는 경우), `$route.hash` 등 유용한 정보를 제공
3.  **_this.\$route.params_** : <u>id의 정보를</u> 얻을 수 있다.
    > user컴포넌트에서 id에 대한 정보를 조회하여, id를 통해 백엔드 데이터를 얻는 것!

## 2. Params 변경 사항에 반응하기 (컴포넌트에 해당)

1. 라우트는 **id**가 변경될 때 **동일한 컴포넌트 인스턴스가 재사용**된다.
   - 이 때문에 라이프 사이클 훅이 호출되지 않는다.
2. created(){}, watch 옵션을 사용하자!

```js
  const User = {
    template : ...,

    watch : {
      `$route` () {
        //경로 변경에 반응
      }
    }
  }
```
