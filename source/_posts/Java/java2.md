---
title: 2. Java 준비 (JDK, JVM, JRE)
date: 2020-09-04 16:07:12
tags: Java
---

# JDK, JVM, JRE

> **java 실행 순서**
> 컴파일단계 (.java 파일을 .class로 컴파일) => 실행단계 (VM에서 .class를 실행)
>
> 1. hello.java 소스 작성
> 2. javac.exe -> hello.class로 컴파일
> 3. JVM(java Virtual Machine) -> class파일의 바이너리 코드를 해석해 프로그램 수행

<br/>

<img src="/images/java.bmp" width="400" alt="java">

## 1. JDK (Java Development Kit)

- java를 사용하기 위한 개발 도구
- 일반적으로 C:\Program Files\Java\ 설치됨
  - \bin javac.exe : (java compolier) java를 컴퓨터가 읽을 수 있게 변역

## 2. JVM (Java Virtual Machine)

- java 가상머신
- class 바이너리 코드 읽기 -> 검증 -> 실행 -> 실행환경의 규격 제공(JRE)
  > - class를 한 번 더 생성함에 따라 속도가 C에 비해 느림 => 이를 통해, 한 번 작성한 파일은 어떤 OS에서도 사용할 수 있다!

## 3. JRE (Java Runtime Environment)

- java 실행 환경
- VM이 자바 프로그램을 동작시킬 때 필요한 라이브러리 파일들과 기타 파일들을 갖고 있다
- JVM의 실행환경을 구현했다고 할 수 있다!
