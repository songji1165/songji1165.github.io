---
title: Vue 기본 문법 1 
date: 2019.04.09
tags: Vue
---

# Vue
- 모든 Vue앱은 **Vue함수**로 새 **Vue 인스턴스**를 만든다.
- 새 Vue 인스턴스 등록 : Vue앱은 **new Vue**를 통해 **루트 Vue 인스턴스**로 구성되어진다.
```js
    var vm = new Vue({
        //루트 Vue 인스턴스
    })
```
> 인스턴스란 .?
- **java**
    - 클래스(설계도)를 바탕으로 여러 개의 다른 모양의 인스턴스(제품)을 만들 수 있다!!

    1. 클래스(Class) : 연관되었 있는 변수와 메소드의 집합이다. -> **설계도**
        ```text
            class Gruop {}
        ```
        - class 키워드로 그룹화하겠다고 선언
        - 클래스 이름으로 그룹의 이름을 부여
        - 중괄호 안에는 연관된 로직들이 들어감
    2. 인스턴스(Instance) : 클래스를 사용하기 위한 제품(부품)정도로 이해하자. -> **제품**
        ```js
            Group g1 = new Group();
            Group g2 = new Group();
        ```    
    - new Group() : 클래스Group을 구체적인 제품으로 만드는 명령어 => **인스턴스**
    - new를 이용해 만든 인스턴스를 변수 g1에 담고 있다.
        -> 변수가 데이터 타입을 담고 있듯이 g1에는 사용자 정의 타입을 담는다.
            => **g1은 Group이라는 클래스를 담고 있다!!**



## 1. 선언적 렌더링(1) : 텍스트보간법 
- 데이터 바인딩의 기본 형태이다.
```text
    <p id="ex">{{message}}</p>
```
```js
    new Vue({
        el : "#ex",
        data : {
            message : '데이터렌더링한다(el로 연동 후 data에 텍스트보간법으로 렌더링)'
        }
    })
```
```text
    hi
```
- el : css선택자처럼 vue선택자정도로 생각하면 된다.
- data : data 객체의 있는 것들은 프록시 처리 된다.
    - 프록시 : 클라이언트와 서버 사이에서 중계한다고 생각하면 된다. data를 거치고 나면 data 안의 속성들이 클란이언트 측으로 보여진다.


## 2. 디렉티브 : v-
- 'v-' 접두사가 있는 특수 속성
- 디렉티브 속성 값은 단일 javajs 표현식이다. (**v-for** 제외)

1. v-if 디렉티브 : 조건부 블록
    - v-if 값이 [TRUE - 보임] [FALSE - 안 보임]
    ```text
        <div id="ifEx">
            <p v-if="seen">{{message}}</p>
            <button @click="clickSeen">클릭</button>
        </div>
    ```
    ```js
        new Vue({
            el : "#if",
            data : {
                message : 'v-on을 통한 클릭메서드 만들기(복수니까 methods)',
                seen : true
            },
            methods : {
                clickSeen : function(){
                    this.seen = !this.seen
                }
            }
        })
    ```
    > v-else, v-else-if도 가능하다. 단, v-if 바로 뒤에 있어야 기능이 가능하다.

2. v-for 디렉티브 : 반복문 블록 
    - item in items 형태의 특별한 문법이 필요
    ```text
        <ul id="iter">
            <li v-for="i in items">{{i.text}}</li>
        </ul>
    ```
    ```js
        new Vue = ({
            el : "#iter",
            data : {
                items : [
                    {text : 1},
                    {text : 2},
                    {text : 3}
                ]
            }
        })
    ```
    - 현재 항목의 index를 부여할 수 있다.
    - v-for 블록 안에는 부모 범위 속성에 대한 모든 권한이 부여된다.
    ```text
        <ul id="iter">
            <li v-for="(i,index) in items">
                {{parentText}} - {{index}} - {{i.text}}
            </li>
        </ul>
    ```
    ```js  
        new Vue({
            el : "#iter",
            data : {
                patentText : '부모 범위 속성 모든 권한',
                items = [
                    {text : js},
                    {text : vue}
                ]
            }
        })
    ```
3. v-model 디렉티브 : 폼입력 바인딩
    - 양방향 데이터 바인딩을 생성
    - input type : text , textarea, checkbox, radio, select ...
    ```text
        <div id="bind">
            <input type="text" v-model="message">
            <p> {{message}} </p>
        </div>
    ```
    ```js
        new Vue({
            el : "#bind",
            data : {
                message = ""
                }
            }
        })
    ```


### 전달인자(:) : 일부 디렉트브는 전달인자(:)를 사용할 수 있다.

1. v-bind:속성="a" : a라는 값을 받아 html 속성을 수정해준다.
    - 약어 : **:속성 = "a"**
    ```text
        <p id="ex" v-bind:title="message">마우스를 올리세요</p>
    ```
    ```js
        new Vue({
            el : "#ex",
            data : {
                message : 'v-bind:title title속성을 데이터렌더링한다 hover시 title'
            }
        })
    ```
    - title속성은 message값과 바인드하여 <p title="message">로 수정된다.


    - 1. v-bind 클래스 바인딩
        - active 클래스 존재 여부는 isActive의 참 속성에 의해 결정된다.
        ```text
            <div v-bind:class="{active:isActive}">
        ```
        ```js
        data : {
            isActive : true
        }  
        ```
    - 2. v-bind 인라인스타일 바인딩 
        - 1. v-bind:style="{font-size:fontSize+'px', color:activeColor}"
            - data : {
                fontSize : 10,
                activeColor : 'red'
                }

        - 2. v-bind:style="styleObject"
            - data : {
                styleObject : {
                    fontSize: '10px',
                    color: 'red',
                }
            }

        
    
2. v-on : v-on은 이벤트핸들링으로 'v-on:이벤트' 전달인자 뒤에 이벤트값이 들어간다.
    - 약어 : **@clcik=""**
```text
    <p id="ex" v-on:click="handleClick">클릭하세요{{message}}</p>
```
```js
    new Vue({
        el : "#ex",
        data : {
            message : ""
        },
        methods : {
            hadleClick : function(){
                this.message = "클릭했다" 
            }
        }
    })
```
