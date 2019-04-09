---
title: 자바스크립트 연산자와 조건문, 반복문 
date: 
tags: javascript
---
# 연산자

1. 사칙연산 (+-*/%)
    - % 나머지 : 2%1 = 0
2. 비교연산자 
    - == (equal operator) : 데이터타입은 달라도 실질적 의미만 같으면 true
    - === (strict operator) : 데이터타입, 실질적의 모두 같아야 true
3. 크기 비교 연산자 (부등호 > < >= <=)
4. and(&&) or(||)연산자
5. 부정연산자 !
    - true, false를 반대로 출력해줌 !, !! 
6. 증감연산자 (++ --)
    1. i++ 후위증감연산자 : i이후 1을 더해 나감
    2. ++i 전위증감연산자 : i+1을 해준 이후 1을 더해 나감

7. **false로 간주되는 값**
    - '' : 빈 값
    - undefined ,var a;(=undefined)
    - null
    - NaN (Not a Number)
    - 0


# 조건문


1. if(**조건-boolean**){} : 만족하는 데이터가 여러개일 경우   
    - if(조건){true} else {false}
    -  if(){} else if {} else {} : 조건문을 좀더 풍부하게 사용할 수 있다.
2. switch(선택문) : 여러 경우의 값 중 일치하는 데이터를                     찾아 그 해당하는 코드를 실행
    ```text
    switch(){
        case 값1 : 코드값;
        break;
        case 값2 : 코드값; 
        break;
        default: false
    }   
    ```

# 반복문

1. while(조건){ 반복 실행할 코드}
    ```text
    var i = 0;

    while(i<10){
        console.log(i);
        i = i+1
    }
    ```
2. **for**(초기화; 반복조건; 반복문이 시작될때마다 실행될 코드){ 반복 실행할 코드 }
    ```text
    for(var i=0; i<10; i++){
        console.log(i)
    }
    ```
3. do{ 반복 실행할 코드 } while (조건) : do가 무조건 한번 실행이 된후 조건에 따라 반복실행이 된다.
