---
title: 0603 - 0605 study
date: 2019-06-05 16:17:12
tags: 개발일기
---

### 오늘 할 것

1. 프로젝트(Vue study Trello)
1. 프로젝트shoppingmall aws 서버 만들기

### 공부한 것

1. 트렐로 보드부분에서 데이터를 전역으로 사용하기 위해 vuex를 사용했다. vuex 사용과정에서 며칠을 버벅거렸다. 헬퍼함수를 통해 actions를 사용해주었다. 이렇게 간단하게 사용해도 되는건가 싶지만 일단 vuex actions으로 서버통신을 하여 보드리스트를 불러오는데 성공했다..
2. shopping mall 프로젝트의 서버를 계속 켜두고 있기 어려워서 aws에 서버를 연동시키는걸 시도해보았다. 데이터를 올리는 것까지는 성공했지만 netlify에서는 http가 지원되지 않아 이 부분에서 HTTP 접근제어 CORS 문제가 발생했다.. 이부분은 해결하기 어려운 것 같다..... 우선 shopping mall 프로젝트의 서버부분은 아쉽지만 이대로 끝내야겠다.

![CorsErr](/images/corsErr.png)

> 1. AWS EC2 로그인
> 2. 인스턴스 시작
> 3. 해당 서버 선택 후 기본값으로 '다음' 클릭클릭
> 4. 다음 클릭 후 '검토및시작'클릭 -> '시작하기'
> 5. 키페어 할당 받기 (저장한 곳 잘 기억해두기! (보안 키값 같은거..))
> 6. 이제 aws 서버를 사용할 준비가 되었다. 터미널이나 git bash등을 이용해서 git clone해주고 사용하기!
>    - 해당 파일로 이동해여 node설치 등을 하면 된다.. (아마존 서버의 공간에 나의 DB를 저장(공유)하게 되는것 .. 기존 서버 설치시 필요한 모듈을 설치해주는 것처럼 똑같이 하면 된다.)
>    - aws에서는 내가 접속하게 될 포트를 열어주는 설정을 해주어야 접근 권한이 생긴다.
