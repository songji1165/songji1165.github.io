---
title: MySQL 기본 문법
date: 2019-05-30 16:27:12
tags: db
---

# MySQL 문법

## 1. **SQL(Structured Query Language)**
 1. DML(Data Manipulation Language)
       - 데이터베이스에 저장된 데이터를 처리하거나 조회, 검색하기 위한 명령어
       - INSERT, UPDATE, DELETE, SELECT 등
 2. DDL(Data Definition Language)
       - 데이터베이스나 테이블 등을 생성, 삭제하거나 그 구조를 변경하기 위한 명령어	
       - CREATE, ALTER, DROP 등
 3.  DCL(Data Control Language)
       - 데이터베이스에 저장된 데이터를 관리하기 위하여 데이터의 보안성 및 무결성 등을 제어하기 위한 명령어	
       - GRANT, REVOKE 등

## 2. 기본 구문
1. 일반적인 구문 뒤에는 세미콜론(`;`)으로 구분한다. 
    - 서버와의 연결을 끊는 구문인 QUIT같은 경우는 제외
2. 대소문자를 구별하지 않는다.
    - **테이블명, 필드의 이름은 대소문자 구문한다 !!**
3. 주석
```js
1. # 한 줄 주석

2. -- 한 줄 주석

3. /* 두 줄

   이상의

   주석 */
```

## 3. 기본 DML
```js
create table cust (
    cust_no number(10),
    cust_name varcher2(15),
    phone varcher2(20)
);

insert into tb_cust ( 1, 'song', '01012341234' );
insert into tb_cust ( 2, 'song', '01012341234' );

update cust 
set cust_name = 'songji'
where cust_no = 2;

delete from cust
where cust_no = 1;

commit;

select * from cust;
```
`# DB 조회 결과` 
_ | cust_no | cust_name | phone
---| :---: | :---: | :---:
1 | 2 | songji | 01012341234
