---
title: MySQL JOIN
date: 2019-05-30 16:27:12
tags: db
---

# MySQL JOIN

## 1. JOIN
- 여러 테이블에서 가져온 레코드를 조합하여 하나의 테이블이나 결과 집합으로 표현
- 보통 SELECT문과 함께 사용

## 2. JOIN 종류
1. **Inner JOIN** 
2. **Left JOIN**
3. **Right JOIN**    

#### 1. INNER JOIN
<img src="http://tcpschool.com/lectures/img_mysql_inner_join.png" width="300">

1. `첫번째테이블 inner join 두번째테이블 on 조건` 
   `첫번째테이블 join 두번째테이블 on 조건` 
2. ON 조건에 만족하는 테이터 출력
3. 일반적으로 많이 사용됨



| \_  | cust_no | cust_name |    phone    |
| --- | :-----: | :-------: | :---------: |
| 1   |    2    |  songji   | 01012341234 |
| \_  | cust_no | cust_name |    phone    |
| --- | :-----: | :-------: | :---------: |
| 1   |    2    |  songji   | 01012341234 |

#### 2. LEFT JOIN
1. `첫번째테이블 left join 두번째테이블 on 조건`
2. ON 절의 조건을 만족하지 않는 경우, 첫 번째 테이블의 필드 값은 그대로 출력,
   두 번째 테이블의 필드 값은 모두 NULL로 출력

#### 3. RIGHT JOIN
1. `첫번째테이블 right join 두번째테이블 on 조건`
2. left와 반대, 두번째 테이블 값은 그대로 출력, 첫번째 테이블은 NULL로 출력
