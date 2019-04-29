---
title: Vue의 기본 기능 2(컴포넌트)
date: 2019-04-14 16:07:12
tags: Vue
---

# Vue 컴포넌트

![컴포넌트](https://kr.vuejs.org/images/components.png)

- 컴포넌트 : 재사용 가능한 html엘리먼트를 캡슐화(부품화)
  1. 유지보수가 쉽다.
  2. 각 컴포넌트들을 첨부해서 사용할 수 있어 재활용성이 높다.
- Vue 컴포넌트는 **Vue**인스턴스이다. -> 모든 옵션 객체 사용 가능
- Vue 컴포넌트는 HTML과 독립적이다(아래 3번 참고)

<br/>

### 1. 전역 컴포넌트 등록 : **Vue.component(tagName, options)**

- Vue 컴포넌트에 사용자 지정 태그 이름은 **케밥케이스**로 사용!

- 컴포넌트가 등록 되면 **인스턴스의 템플릿**에서 **커스텀 엘리먼트**로 사용할 수 있다

```js
Vue.component("my-component", {});
```

```text
    <div id="ex">
        <my-component></my-component>
    </div>
```

- **_렌더링 과정_**

```js
    Vue component('my-component',{
        template: '<div>인스턴스 템플릿</div>'
    })

    new Vue({
        el : '#ex'
    })
```

```text
//인스턴스화 후 커스텀엘리먼트 <my-component>자리에 컴포넌트의 인스턴스템플릿으로 렌더링된다.
    <div id="ex">
        <div>인스턴스 템플릿</div>
    </div>
```

### 2. 지역 등록 : components

- 컴포넌트를 **components 인스턴스 옵션**으로 등록할 수 있다. -> 해당 인스턴스/컴포넌트 범위에서만 사용할 수 있게 만들기 위함.

```js
    var Child = {
        templete: '<div>사용자 정의 컴포넌트</div>'
    }

    new Vue({
        el: "#ex",
        data: {...},
        components : {
            'my-component' : Child
        }
    })
```

```text
    <div id="ex">
        <my-component></my-component>
    </div>
```

### 3. <u>DOM 템플릿 주의사항</u>

- DOM을 템플릿으로 사용할 때 (el옵션으로 엘리먼트를 마운트해야 함), Vue는 컴포넌트의 template 콘텐츠만 가져올 수 있기 때문에 **_제한 사항_**이 있다.
- <u>ul,ol,table,select</u>와 같은 일부 엘리먼트는 그 안에 <ul>li,tr,option</ul>등과 같은 꼭 필요한 자식 엘리먼트가 있어야하기 때문에 제한을 갖게 된다!

> 문제점

```text
    <table>
        <my-component></my-component>
    </table>
    // 렌더링시 에러가 발생함!!!
```

> 해결 방법

1. **is** 특수 속성 사용

```text
    <table>
        <tr is="my-component"></tr>
    </table>
```

2. `<script type="text/x-templete">`
3. **_javascript 인라인 템플릿 문자열_** 가장 선호
4. .vue 컴포넌트

### 4. Vue component의 **_data는 함수_**여야 한다!

- Vue 생성자에 사용할 수 있는 대부분의 옵션은 컴포넌트에서 사용할 수 있다. (data, methods, watch ...)

```js
    Vue component('my-c',{
        data : function(){
            return  { ... }
        }
    })
```

### 5. Vue.js의 부모-자식 컴포넌트 관계

![Vue](https://kr.vuejs.org/images/props-events.png)

#### Vue component는 HTML DOM과 **독립적인 존재**이다.

#### 서로 정보공유를 하려면 <u>바인딩을 시켜줘야</u> 한다.

1. **Props 데이터 전달** : 부모가 자식에게 데이터 전달
   - attribute데이터를 가져와서 template 내에 바인딩 될 수 있게 도와준다.
2. **Emit 이벤트 전달** : 자식이 부모에게 이벤트 전달
   - component내에서 발생한 이벤트를 부모에게 전달해 주어 vue인스턴스와 바인딩 된다.

### 6. Props

#### 1. props 옵션 : 상위 엘리먼트가 하위 컴포넌트로 전달될 수 있다. (위 -> 아래)

```js
Vue.component("child", {
  template: `
        <span>{{ myMessage }}</span>
    `,
  props: ["myMessage"]
});
```

```text
<child my-message="바인딩"></child>
```

```
바인딩
```

> - html 속성은 대소문자를 구분하지 않는다 ! **_HTML -> kebab-case(하이픈 구분)_**

- **_Javascript -> camelCased prop_**

#### 2. 동적 props : v-bind

- `v-bind`를 이용해서 부모데이터와 component데이터를 동적으로 바인딩할 수 있다.

```js
Vue.component('modal-open',{

    // props를 통해서 부모엘리먼트의 modalShow값을 받았다.(true)
    props : ['modalShow'],

    // v-if의 modalShow의 값은 true이다!
    template : `
    <div v-if="modalShow">
    </div>
    `,
    }
})

new Vue({
    el : '#ex',
    data : {
        modalShow : true
    }
})
```

```text
    <modal-open
        v-bind:modal-show = "modalShow"
    ></modal-open>
```

> `v-bind : modal-show = "modalShow"`

- <u>부모의 modalShow(true)값</u>을 <u>컴포넌트의 modalShow가 받게 한다.</u>라는 뜻
- props:['modalShow'] => HTML에서는 <u>modal-show</u>로 표현해 준 것이다.

### 7. Emit

#### 1. **this.\$emit** : 하위 컴포넌트에서 발생된 이벤트를 상위 엘리먼트에게 전달해준다. (아래 -> 위)

```js
Vue.component('modal-open',{

    props : ['modalShow'],

    template : `
    <div v-if="modalShow">
        <button @click="close">이벤트 닫기</button>
    </div>
    `,  // v-on으로 템플릿에 똑같은 방식으로 이벤트를 추가해준다.
    },

    // this.$emit을 통해 modal-show에게 이벤트가 발생되었다는것을 알려주다.
    methods : {
        close : function(){
            this.$emit('modal-close')
        }
    }
})

new Vue({
    el : '#ex',
    data : {
        modalShow : true
    },
    methods : {
        // modalClose 함수를 추가한다.
        modalClose :function(){
            this.modalShow = false
        }
    }
})
```

```text
    <modal-open
        v-bind:modal-show = "modalShow"
        v-on:modal-close = "modalClose"
    ></modal-open>
```

> `v-on : modal-close = "modalClose"`

- <u>컴포넌트가 이벤트를 발생시켰다는 것을 modal-close에 알리고</u> 이것을 통해 <u>modalClose이벤트가 발생 한다.</u>라는 뜻
