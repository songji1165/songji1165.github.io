---
title: npm
date: 2019-05-29 16:07:12
tags: nodejs
---

# npm (Node Package Manager)

[daleseo 블로그 참고](http://www.daleseo.com/js-npm-cli/)

> npm (Node Package Manager)
>
> - 말그대로, **node.js의 패키지 관리자**
> - node.js기반의 javascript로 만든 오픈소스 모듈의 저장소
> - <u>**node.js 설치 시** 자동으로 함께 설치 된다!</u>

<br>

## 1. npm 설치 확인

- `npm -v`

<br>

## 2. npm 기반의 프로젝트 설치

##### 1. 해당 파일로 이동

##### 2. `npm init`

      - `npm init -y` : 기본 값으로 설정

##### 3. <mark>**package.json** 파일이 생성</mark>

- package.json : 해당 프로젝트에 설치된 모듈, 모듈관리, 버정 등의 다양한 정보를 알 수 있다.

<br>

## 3. 패키지 설치

#### `npm install` or `npm i`

- **`npm i *` 를 통해 다양한 패키지를 설치할 수 있다!**

1. **node_modules** 디렉터리 생성
   - node_modules 안에 모듈이 설치된다.
2. **package.json** 확인

   - 'dependencies'에서 추가된 패키지를 확인 할 수 있다.

   ```js
   "dependencies": {
      "hexo": "^3.8.0",
    "hexo-cli": "^1.1.0"
   }
   ```

   `dependencies 항목을 기반으로 'npm i' 입력시 해당 모듈만 자동으로 설치 된다.`

<br>

## 4. script 실행

- script 실행시 반복적으로 실행되는 명령어는 **'package.json'**의 **'scripts'**부분에서 등록할 수 있다.

```js
    {
        ...

        "scripts" : {
            "start" : "json-server --watch db.json"
        }

        ...
    }
```

```js
//cmd
npm run start
```

> <mark>test, start</mark> 명령어의 경우, 자주 사용되기 때문에 <mark>run</mark> 생략 가능!
>
> #### `npm start`

<br>

---

<br>

## 1. 지역설치 전역설치

1. `npm i *` : 지역설치 (기본)
   - 해당 프로젝트에서만 모듈들을 사용하기 위한 것
     - 새로운 프로젝트에서는 npm install을 통해 다시 새로운 모듈을 다운 받아야 한다.
2. `npm i -g *` : 전역설치 (--glovbal)

   - 모든 프로젝트에서 공통으로 사용할 수 있는 패키지로 설치된다.
   - <mark>패키지 버전의 꼬임이 발생할 수 있어 주의하자!</mark>

   <br>

## 2. 패키지 제거

1. 지역 패키지 제거
   `npm uninstall *` or `npm r *`
2. 전역 패키지 제거
   `npm uninstall -g *` or `npm r -g *`

## 3. <mark>npx</npx>

1. 패키지의 설치없이 **일회성**으로 실행하게 한다!
   - 프로젝트의 package.json이나 node_modules에 변화가 없다!
2. **장점**
   1. 불필요한 메모리 낭비를 줄일 수 있다.
   2. 무분별한 글로벌 설치로 인한 패키지 버전 꼬임을 방지할 수 있다.
3. NPM 5.2.0 버전 부터 npx를 실행할 수 있다.
   #### `npx *`
   - 예시 )
     `npx http-server`
