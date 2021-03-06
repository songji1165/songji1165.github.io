---
title: Markdown
date: 2019-05-15 16:07:12
tags: etc
---

# Markdown

> [마크다운 참고 링크 (클릭!)](https://support.squarespace.com/hc/en-us/articles/206543587-Markdown-cheat-sheet) <br>

## 1. 마크다운

- 일반 텍스트 문서의 양식을 편집하는 문법
- 읽고 쓰기 쉽다.
- 확장자 : .md
  <br>

## 2. 사용법

#### 1. 제목

```text
h1 = # 제목1
h2 = ## 제목2
h3 = ### 제목3
...
h6 = ###### 제목6
```

<br>
#### 2. 강조

1. 기울임 : `*italic*`, `_italic_`
2. 두껍게 : `**bold**`, `__bold__`
3. 이탤릭+bold : `***기울임,bold***`
4. highlight : `<mark></mark>`
   <mark>**_강조부분_**</mark>
   <br>

#### 3. 리스트

1. ol

```text
1. 순서있는 리스트
2. 순서있는 리스트
```

2. ul

```text
- 순서없는 리스트
* 순서없는 리스트
+ 순서없는 리스트

===============
sub도 사용가능!

- 상위목차
    1.하위목차
        * 최하위목차
```

<br>
#### 3. 링크

```text
[naver](https://naver.com)
```

<br>
#### 4. 이미지

```text
1. 이미지
![img](이미지링크 또는 이미지파일위치)

2. gif파일
![gif](/images/연습.gif)

==============
1. 이미지 크기조절
<img src="링크" width="300" height="300">

2.이미지에 링크
[![Vue](/images/vue.png)](https://kr.vuejs.org/)
```

<br>
#### 5. 인용문(Blockquotes)

```text
> 인용문을 쓸 수 있다.
>> 하위 인용문도 가능하다.
```

<br>
#### 6. 체크박스

```
- [ ] 체크박스
- [x] 체크박스
```

- [ ] 체크박스
- [x] 체크박스

<br>

#### 7. 줄바꿈

- `<br>` html 태그 사용, 엔터 두번
  <br>

#### 8. 수평선

- 각 기호 3개 이상

```
---
***
___
```

<br>

### 9. 표(Table)

- header셀 구분은 `---`
- 정렬 : `---`, `:---:`, `---:`

```
header | header | header
---|:---:|---:
1 | 테이블 내용 | 주석
2 | 테이블 내용 |
3 | 테이블 내용 | 주석

```

| header |   header    | header |
| ------ | :---------: | -----: |
| 1      | 테이블 내용 |   주석 |
| 2      | 테이블 내용 |
| 3      | 테이블 내용 |   주석 |
