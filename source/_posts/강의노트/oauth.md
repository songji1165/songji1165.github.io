---
title: OAUTH
date: 2019-05-16 16:07:12
tags: 강의노트
---

> 'egoing'님의 'OAuth 인증' 기술 세미나
>
> - 구글 연동을 통해 Oauth인증을 학습할 수 있었다.
> - 학습을 위해 가상의 서버가 필요 [Web Server for Chrome](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb)

# OAUTH

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/OpenIDvs.Pseudo-AuthenticationusingOAuth.svg/768px-OpenIDvs.Pseudo-AuthenticationusingOAuth.svg.png)

- '나의 사용자'의 인증을 통해 그들의 서비스를 대신 사용

1. 일반적 인증의 문제점 : '사용자'의 id,pwd => '나'의 db에 저장 => 사용자 대신 '그들의 서비스' 사용 (ex. 구글캘린더에 사용자의 일정을 올림))
   - 심플하지만 보안이 취약!!
     1. '서비스제공자' 입장에서 보안이 뚫렸다고 인식이 될 수 있다.
     2. 만약 '나'에서 정보 유출이 되면 큰일난다!
2. <mark>해결책 <OAuth></mark>
   - id,pw 대신 서비스의 일부를 일정시간동안만 허용할 수 있는 **권한을 부여**해줌
   - **_임시 비밀번호 Access Token_** : '**사용자**'가 id,pwd로 '**서비스제공자**'에게 인증을 하면 '서비스제공자'는 '**나**'에게 <u>임시 비밀번호</u>를 발급해줌

> OAuth
>
> - 인터넷 사용자들이 비밀번호를 제공하지 않고 다른 웹사이트 상의 자신들의 정보에 대해 웹사이트나 애플리케이션의 접근 권한을 부여할 수 있는 공통적인 수단으로서 사용되는, 접근 위임을 위한 개방형 표준 (위키백과)

<br>

### 1. 장점

1. **ACESS TOKEN** : 임시 비밀번호를 발급해줌

   - 기능이 제한적 => 혹시 누출된다해도 문제가 크지 않음
   - but, 보안에 대해서는 항상 중시해야 함 (ex. 서비스는 https를 사용을 지양)

2. **자동화** : 사용자 모르게 자동적으로 처리해줌
   - 제3자의 서비스를 사용할 수 있는 과정을 자동화로 처리
     <br>

### 2. OAUTH 용어

- Resource : 서비스 자원

1. Resorce Owner : 소비자(Consumer)
2. Resourse Server : 제 3자의 서비스
3. <mark>Client : 서비스를 소비하는 '나'(User)</mark>
4. Client ID : 나의 서비스를 그들의 사이트에 등록 후 발급 받는 ID (사업자번호와 같은것)
5. Client SECRET : Client ID처럼 나의 비밀번호.  
    (공인인증서 같은것 - 절대 노출 되면 안됨!)
   > 프론트에서 활용시 Client Secret을 사용하면 안된다!! 노출되기 쉽기 때문!

<br>

### 3. OAuth 인증 방법 3가지

|  방식   | 난이도        | 활용도          | 보안      |
| :-----: | :------------ | --------------- | --------- |
| widget  | 배우기 쉬움   | 자유롭지 않음   | 안전      |
|   raw   | 배우기 쉬움   | 완전 자유로움   | 안전 X    |
| library | 배우기 어려움 | 비교적 자유로움 | 완전 안전 |

---

# API 키

- <u>클라이언트(나)</u>와 <u>서비스 제공자</u> 사이에서 행해지는 것
- 수동으로 '**클라이언트인 내**'가 '**서비스 제공자**'에게 키(패스워드)를 받아와서 사용함
- oauth 보다 훨씬 간편
- 사용에 있어 제한적이고 보안이 취약하다!
