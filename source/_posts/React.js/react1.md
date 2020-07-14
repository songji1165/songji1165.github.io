---
title: 1. React 시작하기
date: 2020-07-10 16:07:12
tags: React
---

> [ 프레임워크 VS 라이브러리 ]
>
> - 프레임워크 : Application 개발시, 뼈대나 기반을 제공
> - 라이브러리 : 특정 기능에 대한 도구, 함수 등을 정의 해놓은 것
>
> 💡 프레임워크 > 라이브러리

<br/>

# React.js

## 1. React 란? 장점 ?

1.  페이스북에서 개발한 '유저인터페이스 라이브러리'로 비교적 안정성이 보장된다.
2.  **Virtual DOM**을 통해, DOM을 효율적으로 업데이트하여, 어플리케이션의 성능을 향상시킨다.

- Virtual DOM : 가상의 DOM
  1. 실제 소스코드(index.html)에는 컴포넌트 정보가 들어가지 않음
     => html 로드 시 빈 index.html만 그리기 때문에 **굉장히 빠름!**
  2. 가상의 DOM을 그려냄으로써 사용자에게 정보를 제공함
     => react가 component를 html에 삽입함.

3.  컴포넌트를 통해 유지보수와 재사용성이 높아진다.
4.  서버 실핼 중에 변경사항이 바로 적용된다.

<br/>

## 2. React 시작하기

- 웹 브라우저는 react 자체를 이해하지 못함 => webpack, babel, react compile 작업 필요
- 위의 작업을 `create-react-app`이 자동으로 설정해줌

1. react application 만들기

   ```bash
   $ npx create-react-app FOLDER_NAME
   ```

   `package.json 참고해보기`

2. react 서버 실행
   - react application 실행 : 서버 자동 설정해줌!

```bash
$ npm run
```

<img src="https://gblobscdn.gitbook.com/assets%2F-LmntoQaR_UpEAiZTdQt%2F-LngSxAANh1YT80RTL_O%2F-LngVwAdQhHSIAdE_7vl%2Fimage.png?alt=media&token=8b896ff4-db80-4cb6-8ce7-f13ea101ef93" width=300>

<br/>

## 3. React 기본구성

- 불필요한 파일은 지운다!

1. public
   - index.html : 기본 소스코드
2. **src** : 주요 디렉터리
   - App.js : 컴포넌트의 시작 파일
   - index.js : 컴포넌트가 삽입될 위치 선언 파일
     <img src="/images/react1.jpg" width="100" height="180" alt="folder">

## 💡 Class ?

**클래스(설계도)를 바탕으로 여러 개의 다른 모양의 인스턴스(제품)을 만들 수 있다**

1. **클래스(Class)** : 연관되었 있는 변수와 메소드의 집합이다. **<u>설계도</u>**
   - 클래스는 data가 없는 빈 껍데기!
```js
// class : 그룹화하겠다고 선언
class Animal {
  constructor(name) {
    this.speed = 0;
    this.name = name;
  }

  run(speed) {
    this.speed = speed;
    console.log(`${this.name}는 ${this.speed}로 달립니다.`);
  }
}

class Rabbit extends Animal {
  hide() {
    console.log(`${this.name}가 숨었습니다.`);
  }
}

let rabbit = new Rabbit("흰 토끼"); //인스턴스 생성

rabbit.run(5); //흰 토끼는 5속도로 달립니다.
rabbit.hide(); // 흰 토끼가 숨었습니다.
```
- extends : class의 상속기능!

2. **인스턴스(Instance)** : 클래스를 사용하기 위한 제품(부품)정도로 이해하자. **<u>제품</u>**
   ```js
   let whiteRabbit = new Rabbit("흰 토끼");
   let blackRabbit = new Rabbit("검은 토끼");
   ```
   - **new** : 클래스 Rabbit 을 구체적인 제품으로 만드는 명령어. **_인스턴스_**
   - new를 이용해 만든 인스턴스를 변수에 담고 있다.
     - **rabbit이라는 변수는 Rabbit 클래스를 담고 있다!**

3. **컴포넌트(Component)** : 기능별로 나누어 관리하는 것
   - 레고 조립하듯 기능별, 위치별로 나누어 조립하는 개념
   - header.js, button.js, footer.js ....

