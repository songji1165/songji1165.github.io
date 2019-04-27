---
title: Vue Router
date:
tags: Vue
---

# router

## 1. 라우터

- 라우팅 : 각 페이지가 주소에 따라 식별.
- 라우팅의 주체
  1. 서버 라우팅 (동기적) - 네이버, 구글
  2. **브라우저 라우팅** (비동기적) - 구글메일, 트렐로
  - 주소 요청 시 라우팅을 브라우저에서 처리,
  - API를 서버로부터 받아온 후 그 데이터를 화면에 뿌림
- **_Vue.js는 브라우저 라우팅 기능을 구현 할 수 있다!_**

> 라우터 라이브러리 (vue-router) 를 사용하면 복잡하고, 효율적인 화면을 다양하게 구현 할 수 있다.

### 2. 간단한 라우팅 만들기

#### ./webpack.config.js

- webpack : 자바스크립드 모듈을 하나의 파일로 묶어내는 번들러
- **entry 속성** : 각 모듈을 사용하고 있는 **최상위 js파일**을 알 수 있다.
  ![webpack]()

#### ./src/main.js

```js
import Vue from "vue";
import App from "./App.vue";

const Login = { template: "<div>Login Page </div>" }; // 1.

const routes = {
  "/": App,
  "/login": Login // 2.
};

new Vue({
  el: "#app",

  computed: {
    VueComponent() {
      // 4.
      return (
        routes[window.location.pathname] || {
          template: "<div>Page not found. 404</div>"
        }
      );
    }
  },
  render(h) {
    // 3.
    return h(this.VueComponent);
  }
});
```

1. `const Login` , `const routes` : 라우터에 쓰일 상수를 만들어 준다.
2. `routes . "/" : App` : **루트 경로**일때는 <u>앱 컴포넌트</u>로 라우팅
   `routes . "/ login" : Login` : **로그인 경로**일때는 <u>로그인 컴포넌트</u>로 라우팅
3. `render (h) { return h(this.VueComponent) }`  
   `render : h => h(this.VueComponent)`
   : render() 함수는 ViewComponent라는 속성을 인자로 전달해서 h() 함수를 호출한다.
4. `VueComponent()` : 해당 경로에 따라 컴포넌트를 다르게 반환하기 위한 VueComponent함수를 만들어 준다. - `routes[window.location.pathname]` : 라우트맵에서 패스네임에 해당하는 컴포넌트를 반환 - `template: "<div>Page not found. 404</div>"` : 패스네임이 없으면 해당 template를 반환
   > window.location.pathname
   > window의 location 객체 : URL 정보를 가져온다.
   > location의 pathname 속성: URL에서 pathname을 가져온다.

---

> **_render 함수_**
>
> - 뷰인스턴스의 객체 el, data 뿐만 아니라, render속성(render함수)이 있다.
> - **render()** : **DOM 생성 함수** (createElement같은 역할)
> - **함수 h()** : 컴포넌트 설정 객체를 넘겨준다. 즉, h함수를 통해서 인자로 받은 컴포넌트를 구현한다.
> - **render (h) { return h(a) }** : render함수는 a인자를 전달받은 h함수를 호출 => 요청경로에 따라 다른 화면을 구현하는 것
