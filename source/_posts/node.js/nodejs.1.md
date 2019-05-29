---
title: npm
date: 2019-04-29 16:07:12
tags: node.js
---

# npm (Node Package Manager)

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

## 3. `npm install` or `npm i`

1. npm install은 해당 프로젝트에서 모듈들을 사용하기 위한 것이다. (global이 아님)
2. 새로운 프로젝트에서는 npm install을 통해 모듈을 다운 받아야 한다.
3. **`npm i *` 를 통해 다양한 패키지를 설치할 수 있다!**
