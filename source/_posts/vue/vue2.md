---
title: Vue 기본 문법 (컴포넌트)
date: 2019-04-12
tags: 개발일기
---

# Vue 컴포넌트
- 컴포넌트 : 재사용 가능한 html엘리먼트를 캡슐화(부품화)
- Vue 컴포넌트는 **Vue**인스턴스이다. -> 모든 옵션 객체 사용 가능
- Vue 컴포넌트는 HTML과 독립적이다(아래 3번 참고)

### 1. 전역 컴포넌트 등록 : **Vue.component(tagName, options)**
- Vue 컴포넌트에 사용자 지정 태그 이름은 **케밥케이스**로 사용!

- 컴포넌트가 등록 되면 **인스턴스의 템플릿**에서 **커스텀 엘리먼트**로 사용할 수 있다
```js
    Vue.component(***'my-component'***, {

    })
```
```text
    <div id="ex">
        ***<my-component></my-component>***
    </div>
```

- ***렌더링 과정***
```js
    Vue component('my-component',{
        templete: '<div>인스턴스 템플릿</div>'
    })

    new Vue({
        el : '#ex'
    })
```
```text
//인스턴스화 후 <my-component></my-component>자리에 컴포넌트의 **인스턴스templete**으로 렌더링된다.
    <div id="ex">
        ***<div>인스턴스 템플릿</div>***
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
- DOM을 템플릿으로 사용할 때 (el옵션으로 엘리먼트를 마운트했을 때), Vue는 템플릿 콘텐츠만 가져올 수 있기 때문에 ***제한 사항***이 있다.
- <ul>,<ol>,<table>,<select>와 같은 일부 엘리먼트는 그 안에 <li>,<tr>,<option>등과 같은 꼭 필요한 자식 엘리먼트가 있어야하기 때문에 제한을 갖게 된다!
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
  2. <script type="text/x-templete">
  3. ***javascript 인라인 템플릿 문자열*** 가장 선호
  4. .vue 컴포넌트 

### 4. Vue component의 ***data는 함수***여야 한다!
- Vue 생성자에 사용할 수 있는 대부분의 옵션은 컴포넌트에서 사용할 수 있다.
```js
    Vue component('my-c',{
        data : function(){
            return  { ... }
        }
    })
```

### 5. Vue.js의 부모-자식 컴포넌트 관계
![Vue](https://kr.vuejs.org/images/props-events.png)
- Props 데이터 전달 : 부모가 자식에게 데이터 전달
- 