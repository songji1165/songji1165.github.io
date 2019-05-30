---
title: Git
date: 2019-05-15 16:07:12
tags: etc
---

# GIT

<mark>[git backlogo 참고](https://backlog.com/git-tutorial/kr/intro/intro1_1.html)</mark>

> - 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템
> - 소스 코드가 변경된 이력을 쉽게 확인할 수 있고, 특정 시점에 저장된 버전과 비교하거나 특정 시점으로 되돌아갈 수 있다.

## 1. Git 기본

1. 원격 저장소(Remote Repository)
   - 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소
   - <mark>github</mark>
2. 로컬 저장소(Local Repository)
   - 내 PC에 파일이 저장되는 개인 전용 저장소
   - <mark>git</mark>
3. Commit
   - 변경을 기록
   - 시간 순으로 기록되어 과거 변경 이력을 알 수 있다.
   - 커밋 메시지 : 변경하는 내용에 대해 메시지를 남기자 ! 꼭 !
     ![커밋](https://backlog.com/git-tutorial/kr/img/post/intro/capture_intro1_3_1.png)
4. 작업트리와 인덱스
   1. 작업트리(work tree) : 작업하고 있는 영역, 상태
   2. 인덱스/STAGE : 저장소에 올리기 전 STAGE단계에 올려 commit을 준비하는 가상 공간 - commit시 원치 않는 파일을 분리 할 수 있다!
      ![작업트리 인덱스](https://backlog.com/git-tutorial/kr/img/post/intro/capture_intro1_4_1.png)

<br>

## 2. GIT 버전관리 하기

#### 1. `cd 디렉토릭경로` : 해당 디렉티로 이동

- `pwd` : 현재 위치 알려줌
- `git` : 사용 가능한 명령어 리스트

#### 2. **`git init`** : git의 저장소 초기화

- **.git** 파일 생성됨 : 현재 디렉토리에 git 작업을 진행할 준비가 됬다.

#### 4. git 버전관리 하기

1.  **`git pull origin master`** : 로컬저장소 local master 최신상태로 만들기
2.  **`git add 파일이름`**
    - **`git add .`** : git이 버전관리 할 수 있도록 명령
3.  **`git status`** : 현재 버전관리 상태를 나타냄
4.  **`git commit -m "message"`** : 커밋 메시지 입력과 함께 커밋

> [ 처음 사용시 자신의 정보 셋팅 필요 ]
>
> 1. git config --global user.name
> 2. git config --global user.email

<br>

## 3. github(원격 저장소)와 git

1. github repository(원격 저장소)와 연결
   **`git remote add origin github주소`** - 해당 github repository의 http나 ssh 주소 입력

2. github repository(원격 저장소)와 복제
   **`git clone github주소`** - 협업시에 원격 저장소에 push하는 것 주의! -> commit 충돌이 될 수 있다! -> **git branch** 사용 권장 - <mark>pull -> commit -> push</mark>
3. github repository(원격 저장소) PULL
   **`git pull origin master`** - 협업 시 원격 저장소에서 최신 변경 이력을 다운로드하여 내 로컬 저장해주어야 한다.

4. github repository(원격 저장소)에 push
   **`git push origin master`** or **`git push origin branch-name`**

<br>

#### 3. git branch

- **작업공간(work tree)를 분리**하여 같은 소스코드를 갖고 다른 작업을 수행할 수 있게 한다.
- 각 브랜치는 다른 브랜치에 영향을 받지 않는다.
- **master** : git의 메인 브랜치

1. git branch 생성
1. **`git checkout -b 브랜치네임`** : 새로운 브랜치 생성
1. **`git checkout 브랜치네임`** : 행당 브랜치로 이동
1. **`git branch`** : 현재 checkout하고 있는 branch 확인
1. git branch push
   - github에서 **merge**를 해줘야 최종적으로 메인 저장소에 저장된다.
