---
title: 0408
date: 2019-04-08 13:20:00
tags: 개발일기
---



### 오늘 할 것 
 1. 개발 블로그 만들기
 2. javascript 개념 정리하기
 3. vue 개념 정리하기
 4. nomad 강의 듣기

### 1. 개발 블로그 만들기
- hexo를 이용하여 github 블로그를 만들었다.
  [Olaf's blog](https://appear.github.io/2018/12/09/ETC/hexo-blog/)를 참고하여 만들었다.

- 블로그 글을 깃헙에 올려서 백업을 해주고 
      블로그 배포를 해주자!  

    1. **github에 프로젝트 올리기**
        - git init : 새로운 local repository 생성
        - git add : 변경된 파일 local repository에 추가
        - git commit : add한 파일을 local repository에 저장
        - git push : local repository를 remote repository(github repository)에 업로드

        1. 작업할 폴더로 이동한다 ! 
            git 해당파일
        2. git add . 
        3. git commit -m "message"
        4. git push origin build  ->branch이름 (일반적으로 master)

    2. **gitblog에 글 올리기**
        - hexo-deployer-git : 블로그로 배포하기  위한 모듈
        - hexo clean : 기존 파일 삭제
        - hexo genarate(=hexo g) : 파일 받아와서 파일 재생성
        - hexo deploy(=hexo d) : 파일 블로그에 배포

        1. npm install hexo-deployer-git
        2. hexo clean
        3. hexo g
        4. hexo d


> git 버전관리와 프로젝트 올리는 방법에 대해 추가적인 공부가 필요할 것 같다

    
### 내일 할 일
1. javascript 개념정리한 것 수정
2. vue 개념 정리 및 복습
3. nomad api 복습 및 개념 정리

> 



