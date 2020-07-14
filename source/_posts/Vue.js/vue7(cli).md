---
title: 7. Vue CLI
date: 2019-04-19 16:07:12
tags: Vue
---

# Vue CLI

#### vue cli : vue 개발환경

## 1. Vue CLI 설치

1. 준비사항 **_node.js_** (node.js는 js를 터미널을 통해 실행할 수 있게 해준다.)

   - 설치 완료 후
     `node -v`
     : node 버전확인

2. `npm install -g @vue/cli`
   : cli 설치

   - error발생 시 : 관리자 권한 필요
     `sudo npm install -g @vue/cli`

3. `vue --version`
   : vue 버전 확인

4. `vue create vue-project`
   : vue 프로젝트 생성(vue-project)

   > cd 로 해당 경로로 이동 후 프로젝트를 생성해준다.

   - cli플러그인 설정 : 개발환경에 대한 디테일을 설정할 수 있다
     > vuex,
     > css pre-processors,
     > linter/formatter,
     > babel -> enter
     > less ->enter
     > pretter
     > lint on save
     > packge.json
     > N.. 로 설정해주면 된다.

5. `npm run serve`
   : 런타임 서버 실행
   - **_localhost:8080_** 의 주소값을 받으면 실행 성공!

## 2. CLI 플러그인 : 개발환경 디테일을 수정할 때 플러그인을 설치하면 된다

- cli 3.0에서부터는 간단하게 플러그인을 설치하여 바로 적용할 수 있다.
- `vue add vuetify` 같이 플러그인을 설치할 수 있다.
- 플러그인 설치 완료 :
  1. **main.js 파일**에 `import './plugins/vuetify'`라고 항목이 추가 된다.
  2. **plugins 폴더**에 **vuetify라는 파일이 생성**된다.
  3. 그 외에도 변경된 것을 살펴볼 수 있다.

## 3. 중요 파일

1. main.js : 해당 프로젝트의 어플리케이션을 구동시켜주는 main
2. router.js : 라우터 조절
3. store.js : 전역상태 값을 조절
4. App.vue : 기본 파일 (가장 껍데기)

#### App.vue

1. `<template></temlate>`
   - template속성 안에는 html속성이 들어가면 된다.
2. `<script></script>`
   - **_exprot default{}_** : **모듈을 추출한다. 내보낸다.**
     - component안의 옵션처럼 동일하게 작성하면 된다.
     - component의 `data`는 함수형식을 선언!

```js
    <template>
        <div>
            <p>
                {{title}}
            </p>
        </div>
    </template>

    <script>
        export defualt {
            name:'app',
            data () {
                return {
                    title : 'hi'
                }
            },
            methods : ....
        }
    </script>
```

#### main.js

1. `import 컴포넌트명 from './App.vue'`

   - export된 값을 import한다. 즉, **모듈값을 받아들인다.**
   - 컴포넌트명 : 해당파일에서 사용할 컴포넌트이름
   - '파일 경로' : './' 이면 같은 경로

2. `new Vue({})`
   - 선언된 Vue어플리케이션을 통해 전체 어플리케이션이 작동하게 된다.

```js
import App from "./App";
//App.vue  -> .vue는 생략 가능

new Vue({
  router,
  store,
  render: h => h(App)
}).$mount("#app");
```

> - export 컴포넌트명 from '파일경로' : 모듈을 내보낸다.
> - import 컴포넌트명 from '파일경로' : 모듈을 받는다.
