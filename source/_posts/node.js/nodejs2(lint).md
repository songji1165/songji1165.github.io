---
title: ESLint
date: 2019-05-30 16:07:12
tags: nodejs
---

# ESLint

## 1. ESLint

1.  **Lint** : 소스코드를 분석하여 프로그램 오류, 버그, 스타일 오류, 의심스러운 구조체에 표시를 달아놓기 위한 도구
    **`ESLint : EcamaScript, 자바스크립트의 문법 오류와 스타일 오류 등을 분석할 수 있다.`**
2.  장점
    1. 협업에 있어 코딩 스타일 통일성을 갖출 수 있다.
    2. 오류를 쉽게 찾을 수 있다.
    3. 확장성이 좋다. (개별 Linting Rule을 추가할 수 있다.)

<br>

## 2. ESLint 설치

#### 1. 해당 프로젝트 이동 후

        `npm init -y`

#### 2. `npm install -g eslint`

- 전역으로 eslint 설치
- `npx eslint --init`나 `npm i eslint`로 설치해도 무방

#### 3. 선택사항 선택 후, <mark>Y</mark>로 선택사항 저장

![img](/images/lint.jpg)

#### 4. 프로젝트 루트에 `.eslintrc.js`파일 생성됨

- **.eslintrc.js** : eslint 설정이나 옵션을 추가, 설정할 수 있다.

<br>

## 2. ESLint 검사

#### 1. 검사

`npm run lint` or `npm esling "*.js"`

#### 2. 수정

`npm run lint --fix` or `npm eslint "*.js" --fix`
