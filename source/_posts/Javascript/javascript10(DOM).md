---
title: 자바스크립트 DOM
date: 2019-04-22 16:07:12
tags: javascript
---

# DOM (Document Object Model)

> 1. 브라우저의 렌더링 엔진이 HTML을 브라우저가 이해할 수 있는 구조로 메모리에 적재
> 2. 브라우저의 렌더링 엔진이 HTML의 계층적 구조를 브라우저가 이해할 수 있는 <u>객체</u>로 만들어 **트리구조(DOM TREE)**로 구조화

<br>

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .red {
        color: #ff0000;
      }
      .blue {
        color: #0000ff;
      }
    </style>
  </head>
  <body>
    <div>
      <h1>Cities</h1>
      <ul>
        <li id="one" class="red">Seoul</li>
        <li id="two" class="red">London</li>
        <li id="three" class="red">Newyork</li>
        <li id="four">Tokyo</li>
      </ul>
    </div>
  </body>
</html>
```

![DOMTREE](https://poiemaweb.com/img/dom-tree.png)

<br>

## 1. DOM tree

`Document Node, Element Node, Attribute Node, Text Node`

1. 문서노드 (Document Node)

   - 트리의 최상위
   - 각각 요소, 어트리뷰트, 텍스트에 접근하려면 문서 노드를 통해야 한다.
   - `window`

2. 요소노드 (Element Node)

   - HTML요소를 표현
   - 문서의 구조를 서술
   - 어트리뷰트, 텍스트는 요소별 특성을 표현하기 위해 HTML Element객체를 상속한 객체로 구성된다.
   - `window.document`

3. 어트리뷰트 노드(Attribute Node)

   - HTML 요소의 어트리뷰트(속성)
   - 어트리뷰트 노드는 해당 요소의 일부
   - 해당 요소 노드를 찾아 접근하면 어트리뷰트를 참조, 수정 할 수 있다.
   - `window.document.getElementById`

4. 텍스트 노드(Text Node)
   - HTML 요소의 텍스트 표현
   - 요소노드의 자식
   - DOM tree의 최종단
   - `안녕하세요`

<br>

## 2. DOM 접근

> 1. 조작하고자하는 요소를 선택, 탐색
> 2. 선택된 요소의 콘텐츠 또는 어트리뷰트를 조작

#### 1. DOM 선택

![DOM](https://poiemaweb.com/img/select-an-individual-element-node.png)

1. 단일 선택
   1. `document.getElementById('id')`
   2. `document.querySelectio('cssSelector')`
   - 여러 개의 요소가 있을 경우 가장 첫번째 요소 선택
2. 다중 선택
   1. `document.getElementsByClassName('class')` (ie9)
   2. `document.getElementsByTagName('TagName')`
   3. `document.querySelectorAll(Selector)`
      <br>

#### 2. DOM 탐색

- DOM 선택 후

  1. `.parentNode`
  2. `.childNodes`
  3. `.firstChild`, `.lastChild`
  4. `.hasChildNodes()` : 자식 노드 있는지 확인 Boolean
  5. `.children` : child노드의 자식 노드의 컬렉션 반환 (IE9)
  6. `.previousSibling`, `.nextSibling` : 형제 노드 탐색(IE9)
     <br>

#### 3. DOM 조작

- DOM 선택/탐색 후

1. 어트리뷰트의 값을 취득 또는 변경할 수 있다.
   1. `.className = "red"`
   2. `.id = "red"`
   3. `.innerText = 'red'`
   4. `.innerHTML = '<span>red</span>'`
2. 어트리뷰트의 값을 검사, 취득, 설정, 제거
   1. `.hasAttribute(attribute)` : return boolean 값 검사
   2. `.getAttribute(attribute)` : 값 취득
   3. `.setAttribute(attribute, value)` : 값 설정
   4. `.removeAttribute(attribute)` : 값 제거
3. DOM 직접 조작해서 새로운 요소 추가
   1. `document.createElement('tagName')`
   2. `document.createTextNode('text')`
   3. `document.appendchild('Node')`
   4. `document.removeChild('Node')`
      <br>

## 3. STYLE

1. style 프로퍼티 : inline 스타일 선언을 생성, 지정
    - `document.getElementById('el').style.color = 'red'`
3. style 프로퍼티 값 취득 : `window.getComputedStyle`
   - `var width = window.getStyle(el, 'width')`
