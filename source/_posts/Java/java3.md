---
title: 3. Java Hello World 출력
date: 2020-09-06 16:07:12
tags: Java
---

# Java로 Hello World 첫 출력!

<br/>

## 1. JDK 설치

- Java를 사용하기 위해 필요한 필수 개발환경
- [Oracle - JDK 설치](https://www.oracle.com/java/technologies/javase-downloads.html)

## 2. Java 환경변수 설정

##### 1. 내 컴퓨터 - 고급설정 - 환경변수

- PATH에 C:\Program Files\Java\jdk-14.0.2\bin 추가하기
  <img src="/images/path.bmp" height="250" alt="PATH">

##### 2. terminal창에 **javac** 실행해보기

```bash
  C:\Users\song> javac
```

- 해당 문구 나오면 성공
  <img src="/images/cmd.bmp" width="500" alt="javac">

> 아래의 에러일 경우 환경변수 다시 잡기!
>
> ```bash
> 'javac'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는 배치 파일이 아닙니다.
> ```

##### 3. java 소스 만들기

```java
// HelloWorld.java

public class HelloWorld {
        public static void main(String[ ] args) {
                System.out.println("Hello World!");
        }
}
```

> public class일 경우, class 명과 java 파일명이 같아야 한다.

##### 4. java -> class 파일로 컴파일

```bash
  C:\Users\song> javac HelloWorld.java
```

- 아무런 문구가 없다면 class 컴파일 성공

##### 5. class 파일 실행해보기

```bash
  C:\Users\song> java HelloWorld
```

<img src="/images/javaHello.PNG" width="250" alt="helloWorld">
