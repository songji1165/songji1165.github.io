---
title: node.js란
date:
tags: node.js
---

# node.js란

> 웹브라우저 환경 > html을 이용 > <u>웹 어플리케이션</u>을 만든다.

- node.js환경 > javascript를 이용 > <u>웹어플리케이션</u>을 만든다.
- (node.js를 사용해서 웹어플리케이션을 만든 것)

# node.js

- **_자바스크립트 런타임 환경_**

  - 런타임 : 프로그래밍 언어가 구동되는 환경
  - 런타임 환경 : 프로그램을 위한 소프트웨어 서비스를 제공하는 가상 머신의 상태

- **javascript라는 언어**로 **node.js런타임 프로그램을 실행**시켜 **node.js 애플리케이션**을 만든다
- javasctipt를 통해서 node.js가 갖고 있는 기능을 실행하여 웹어플리케이션(웹브라우저)을 만든다. (즉, node.js로 웹어플리케이션을 만든것)

- javascript를 이용해서 웹브라우저뿐만 아니라 웹서버를 조작할 수 있다.

### node.js 설치하기

1. node.js홈페이지에서 파일 다운로드

2. 그 후 node.js가 잘 설치되있는지 확인

   1. cmd 터미널콘솔을 실행시키기
   2. `node -v`
      후 **버전정보**가 뜨면 설치 성공!
   3. `node`
      node런타임환경을 이용해 **javascrip를 입력**할수 있다.
   4. console.log(1+1) 을 써본 후 화면 출력이 잘되는 지 실행해 본다.
   5. <u>node 런타임 환경을 나갈 때에는</u> **ctrl+c** 를 누르거나 **.exit**을 치면된다.

3. javscript 파일 실행시키시기
   1. `cd`
      (change directory) 후 이동하려는 파일경로를 써주면 된다.
      - (예 : cd C:\Users\eumji\Desktop\vue-todo)
   2. `dir`
      현재 디렉토리에 존재하는 파일들을 보여준다.
   3. `node 파일이름.js`
      js파일을 실행시켜서 런타임 환경에서 보여준다.

### url 구조

`http://opentutorials.org:3000/main?id=HTML&page=12`

1. http

   - 프로토콜 통신규칙 : 웹브라우저와 웹서버과 데이터를 주고받기 위한 통신 규칙

2. opentutorials.org

   - host(domain) : 특정한 인터넷에 연결되어 있는 컴퓨터를 가르키는 주소

3. 3000

   - port : 서버의 주소
   - 기본 port : 80 (기본 port값 생략 가능)

4. main

   - path : 컴퓨터 안의 어떤 디렉토리의 어떤 파일을 나타냄

5. **?id=HTML&page=12**
   - qeury string : 웹서버에게 읽고싶은 데이터의 정보를 전달하는 역할
