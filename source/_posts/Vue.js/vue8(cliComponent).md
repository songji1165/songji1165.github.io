---
title: 8. Vue CLI Component
date: 2019-04-19 16:17:12
tags: Vue
---

# Vue CLI Component

## 1. CLI Component 등록 방법 : **_지역_** component 등록

1. 새로운 파일 추가 (**Home.vue**)

```js
    <template>
        <div>
            <h1>{{ homeTitle }}</h1>
        </div>
    </template>


    <script>
        export default{
            data () {
                return {
                    homeTitle : '홈 입니다.'
                }
            }
        }
    </script>
```

2. **Vue.app**

```js
    <template>
        <div>
            <h1>{{ title }}</h1>
            <HomeComponent></HomeComponent>
        </div>
    </template>


    <script>
            // 컴포넌트명'HomeComponent' : Vue.app에서 사용할 이름
        import HomeComponent from './Home.vue'


        export default{
                // HomeComponent를 갖고온 후 이것을 사용하기 위해서 이것은 컴포넌트야라는 선언이 필요!
            components : {
                HomeComponent
            },

            data () {
                return {
                    title : 'Vue 최종 껍데기'
                }
            }
        }
    </script>
```

## 2. CLI Component 등록 방법 : **_전역_** component 등록

- 전역 Component의 사용 : <u>footer나 navigation 부분 등 공통적으로</u> 여러 파일에 넣어줘야 할 때, 일일이 import를 작성하기 번거롭기 때문에 _전역으로 한번만 등록_

1. 새로운 파일 추가 (**Home.vue**)

```js
    <template>
        <div>
            <h1>{{ title }}</h1>
            <AppHome></AppHome>
        </div>
    </template>


    <script>
    export default{
        data () {
            return {
                title : 'Vue 최종 껍데기'
            }
        }
    }
    </script>

```

2. **main.js**

- main.js : 어플리케이션을 관장(책임자)해주는 역할
- main.js에 전역으로 컴포넌트를 만들어주면 모든 파일에서 `<AppHome></AppHome>`만 추가해주면 컴포넌트 사용이 가능하다.

```js
import HomeComponent from "./Home.vue";

Vue.component("AppHome", HomeComponent);

new Vue({});
```
