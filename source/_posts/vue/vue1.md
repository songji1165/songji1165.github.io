---
title: Vue
date: 2019.04.09
tags: Vue
---

# Vue
> Vue 장점
    1. 학습곡선이 낮다.
    2. Vue의 핵심인 컴포넌트를 통해 유지보수와 재사용성이 높아진다.
    3. DOM조작인 jquery같이 쉬운 편이다.
    4. 요소를 실시간으로 반응시킬 수 있다. 
<br/>

## Vue 시작하기
- JS라이브러리 사용하듯 script를 붙여넣기하면 된다.

1. 도움되는 콘솔 경고를 포함한 개발 버전
    ```js
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    ```

2. 상용버전, 속도와 용량이 최적화된 버전
    ```js
    <script src="https://cdn.jsdelivr.net/npm/vue"></script>
    ```


## Vue 앱 사용하기
- **Vue함수** :  모든 Vue앱은 **Vue함수**로 새 **Vue 인스턴스**를 만든다.

- 새 Vue 인스턴스 등록 : Vue앱은 **new Vue**를 통해 **루트 Vue 인스턴스**로 구성되어진다.
```js
    var vm = new Vue({
        //루트 Vue 인스턴스
    })
```


### 인스턴스란 .?
##### ***Java***
- ***클래스(설계도)를 바탕으로 여러 개의 다른 모양의 인스턴스(제품)을 만들 수 있다***
    1. **클래스(Class)** : 연관되었 있는 변수와 메소드의 집합이다.  **<u>설계도</u>**
        ```js
            class Gruop {}
        ```
        - **class키워드** : 그룹화하겠다고 선언
        - **클래스 이름** : 그룹의 이름을 부여
        - **중괄호** : 중괄호 안에는 연관된 로직들이 들어감
    2. **인스턴스(Instance)** : 클래스를 사용하기 위한 제품(부품)정도로 이해하자. **<u>제품</u>**
        ```js
            Group g1 = new Group()
            Group g2 = new Group()
        ```
        - **new Group()** : 클래스Group을 구체적인 제품으로 만드는 명령어. ***인스턴스***
        - new를 이용해 만든 인스턴스를 변수 g1에 담고 있다.
            - 변수가 데이터 타입을 담고 있듯이 g1에는 사용자 정의 타입을 담는다.
                - **g1은 Group이라는 클래스를 담고 있다!!**