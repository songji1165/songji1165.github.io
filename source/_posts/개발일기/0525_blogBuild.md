---
title: 0525 study
date: 2019-05-25 16:17:12
tags: 개발일기
---

### 오늘 할 것

1. hexo 오류 해결 -> node 재설치

### 공부한 것

1. 하루하고 반나절을 예상치 못한 버그로 삽질을 했다. 얼추 버그에 원인으로는 버전의 꼬임이었던 것 같다.. 아직도 어디서 내가 잘못 건드린지는 모르겟으나 무분별한 패치나 버전 업그레이드로 인해 각 패키지에서 필요로 하는 버전과 맞지 않다는 것 같다.. 언제부터 버전이 꼬인건지 모르기 때문에 node를 삭제하고 재설치하는 것이 더 빠를거라 판단되어 결국 재설치를 해보았다. 그 결과 한방에 해결 되었다. 생각보다 너무나 간단하게 해결되었다.

   - 글로벌 install : 용량 차지, 새로운 버전 설치시 이미 존재하는 패키치들의 버전과 꼬일 수 있다. 등의 문제가 생길 수 있다
     -> **npx 활용하자**

   > [npm 글로벌 설치 문제 참고](https://geonlee.tistory.com/32)

- [나와 같은 문제를 겪은 블로그 글을 발견했다.. 나도 이것저것 해본다고 하다 캐시를 잘못 건드려 무언가 많이 꼬인 것 같다. (클릭)](https://ellapresso.tistory.com/m/27?category=777454)

- [hexo issue github (클릭)](https://github.com/hexojs/hexo/issues/3546)

![npmErr](/images/npmEr0.png)
![npmErr](/images/npmEr1.png)
![npmErr](/images/npmEr.png)

> node.js 삭제
>
> 1. window '프로그램 제거 또는 변경'으로 이동
> 2. node.js 검색
> 3. 삭제 실행

### 내일 할 것

1. 자바스크립트 이론 공부
2. 프로젝트(Vue study Trello)
3. 자소서 정리
4. 알고리즘
