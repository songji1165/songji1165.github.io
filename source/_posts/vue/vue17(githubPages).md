---
title: 16. Vue Cli Github Pages
date: 2019-05-19 16:07:12
tags: Vue
---

# Vue Cli Github Pages

> [Vue Cli Github Pages ](https://medium.com/@Roli_Dori/deploy-vue-cli-3-project-to-github-pages-ebeda0705fbd)(참고)

<br>

## 1. Github Pages

1. github에서 제공하는 사이트 호스팅 서비스
   - github repositories의 소스코드를 기반으로 웹사이트 생성
2. 커스텀 url을 무료 제공
   - 웹사이트 기본 url : `https://UserName.github.io`
3. 서버쪽 코드는 제공되지 않음!

<br>

## 2. Vue Cli 프로젝트를 Github Pages로 배포하기

`github 저장소에 소스코드가 올려진 repositories 기준`

<img src="/images/vueclipages.jpg" width="300">

<br>

#### 1. Vue Cli 프로젝트에 새로운 브랜치 'gh-pages' 생성

    `git checkout -b gh-pages`

<br>
#### 2. 프로젝트 루트 디렉토리에 새로운 파일 <mark>'vue.config.js'</mark> 추가
<br>
#### 3. vue.config.js에 다음과 같이 작성

```js
// vue.config.js

module.exports = {
  publicPath: "/pages"
  // 프로젝트 이름 쓰기
};
```

<br>

#### 4. .gitignore 파일에서 <mark>/dist</makr>를 주석 처리

- dist 파일을 버전관리하기 위함
  <img src="/images/pagesdist.jpg" width="200">
  > dist (distribute) 파일
  >
  > - 배포될 파일들이 들어 있는 디렉토리

<br>

#### 5. dist 파일 생성

`npm run dist`

<br>

#### 6. subtree로 작업하기

> [subtree참고 페이지](https://select995.netlify.com/git/git-subtree)
>
> - **subtree** : 한 저장소에 여러 저장소를 통합하는 개념
>   - 장점 : 한 저장소에서 여러 저장소를 통합 관리할 수 있다.
>   - 단점 : Subtree Push를 하려면 --prefix 옵션을 사용해야 한다. (하위 저장소의 경로를 기억해야 한다.)

1. dist 파일의 존재를 git에게 알리기 1. `git add dist` 2. `git commit -m "Initial dist subtree commit"`
   <br>

2. **git subtree 추가**

```text
git subtree push --prefix dist origin gh-pages

 // -> dist 디렉토리를 gh-pages브랜치에 push 함
```

<br>

#### 7. github 저장소에서 '_settings_'으로 이동

![img](https://cdn-images-1.medium.com/max/1200/1*OtBpNJyBls1kEjQIDDXhqA.png)

<br>

#### 8. 밑으로 스크롤 하여 '_GitHub Pages_'의 source를 <mark>'gh-pages branch'</mark>로 변경

<img src="/images/distsucc.jpg" width="300">

#### gh-pages branch로 변경하면 (2)에 url이 나타나면 배포 성공!
