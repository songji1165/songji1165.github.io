---
title: 5. Vue DOM
date: 2019-04-14 16:17:12
tags: Vue
---

# 1. Vue 옵션 DOM

## 1. el

1. **new**를 이용한 인스턴스 생성때만 사용
2. css선택자로 Vue 인스턴스와 DOM 마운트

## 2. template

- 문자열 템플릿 : Vue 인스턴스의 마크업

## 3. render

- 문자열 템플릿 대신 완전한 javascript프로그래밍이 필요할 때

```js
<template>
  <div>
    <h1> {{ blogTitle }} </h1>
  </div>
</template>

 ...

 render : function (createElement) {
   return createElement('h1', this.blogTitle)
 }
```
