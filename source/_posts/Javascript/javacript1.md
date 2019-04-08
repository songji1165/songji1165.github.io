---
title: 자바스크립트 동작원리
date: 
tags: javascript
---

# 자바스크립트 동작원리 
1. (html 마크업 -> html파서) + (css 마크업 -> css파서) => 렌더링 트리

    - html파서 (html 문서 해석기 ) :
                 html파서를 통해 html문서를 읽은 후 DOM트리를 형성 함.
    - css 파서 (css 문서 해석기 ) : 
                 css는 html에 시각적인 스타일을 입힘 
    - 렌더링 트리 : 페이지에 렌더링  
                즉, html문서와 css문서를 시각적인 구성요소로 트리 내용 순서대로 페이지를 그려냄  
2. ** javascript는 렌더링 엔진이 아닌 javascript엔진에서 처리 됨 **
    - html파서가 중간에 javascript를 만나면 javascript엔진으로 넘어가서 DOM생성을   
          중지하게 됨 

![자바스트립트 동작 원리](https://d2.naver.com/content/images/2015/06/helloworld-59361-3.png)

