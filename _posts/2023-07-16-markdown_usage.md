---
title: \[Jekyll Blog\] 마크다운(Markdown) 사용법 및 예제
header: header
toc: true
toc_sticky: true
toc_label: Contents
excerpt: Markdown usage from theorydb.github.io
date: 2023-07-16
categories:
    - tests
---
<!--bundle exec jekyll serve-->


<a id = "markdown의-반드시-알아야-하는-문법">nyong</a>

<a href = "https://theorydb.github.io/envops/2019/05/22/envops-blog-how-to-use-md/#markdown%EC%9D%98-%EB%B0%98%EB%93%9C%EC%8B%9C-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%98%EB%8A%94-%EB%AC%B8%EB%B2%95" target='_blank'> 이 사이트를 그대로 따라해보았다. </a>

### 개요

<!--이건 따옴표가 아닌 다른 `로 둘러싼 것이다!-->
지금 당장 필요한 `마크다운(Markdown)` 문법부터 단계적으로 배워봅시다.

- 목차
  - Markdown이란?
  - Markdown 에디터 뭐 쓸까?
  - Markdown 문법1(반드시 알아야 하는)
  - Markdown 문법2(유용한 부가기능)
  - 실전연습
  - 이미지를 쉽게 업로드 하는 방법
  - 소소한 Tip 그리고 고장났을 때

### Markdown이란?

Markdown은 문서 작성을 지원하는 Tag 형식의 문법이다.



### Markdown 에디터 뭐 쓸까?

### Markdown 문법1(반드시 알아야 하는)

#### [1단계] `헤더(Header)`: 제목, 문단별 제목을 쓰고 싶을 때

글의 구조(개요) 및 큰 틀을 잡을 때 사용한다.

<!-- 이건 pre 태그!-->
<pre>
# 제목 1단계
## 제목 2단계
### 제목 3단계
#### 제목 4단계
##### 제목 5단계
###### 제목 6단계
</pre>

# 제목 1단계
## 제목 2단계
### 제목 3단계
#### 제목 4단계
##### 제목 5단계
###### 제목 6단계

#### [2단계] `수평선`: 내용을 명시적으로 구분하고 싶을 때

<pre>---</pre><br>
---

#### [3단계] `엔터키(줄바꿈, 개행)`: 라인을 바꾸고 싶을 때

<pre>
Enter 2번을 입력하면.(from)

(to)< !-- from과 to 사이 Enter 2번 입력--> 문단이 바뀐다. < !--편의상 주석 앞에 띄어쓰기를 했당 안하면 출력되더라-->

줄바꿈은 하고 싶은 문장 마지막에 \<br\> 태그를 쓸 수 있다. < !--얘도 출력되서 띄어쓰기 한 거임 코드에 넣을 때는 꼭 붙여서 넣기!-->

(from)<span><b</span><span>r></span>
(to)
</pre>

Enter 2번을 입력하면.(from)

(to)<!-- from과 to 사이 Enter 2번 입력--> 문단이 바뀐다. <!--편의상 주석 앞에 띄어쓰기를 했당 안하면 출력되더라-->

줄바꿈은 하고 싶은 문장 마지막에 \<br\> 태그를 쓸 수 있다. <!--얘도 출력되서 띄어쓰기 한 거임 코드에 넣을 때는 꼭 붙여서 넣기!-->

(from)<br>
(to)

#### [4단계] `목록(List)` 요소를 나열할 때

<pre>
1. 첫번째 ordered list, ol
1. 두번째
1. 세번째

+ 순서없는 리스트 unordered list, ul
  - 홍길동
    * 중대장
      + 프로실망러
</pre>

1. 첫번째 ordered list, ol
1. 두번째
1. 세번째

+ 순서없는 리스트 unordered list, ul
  - 홍길동
    * 중대장
      + 프로실망러

#### [5단계] `강조`: 문장 내 강조하고 싶은 단어를 눈에 띄게

<pre>
__bold__<span><b</span><span>r></span>
**bold**<span><b</span><span>r></span> <!--ctrl+b with extension-->
<span><b</span>>bold<<span>/b><b</span><span>r></span>
_italic_<span><b</span><span>r></span>
*italic*<span><b</span><span>r></span> <!--ctrl+i with extension-->
<span><i</span>>italic<<span>/i><b</span><span>r></span>
<span><u</span>>underline<<span>/u><b</span><span>r></span>
~~breakthrough~~<span><b</span><span>r></span> <!--alt+s on windows-->
__bold and *italic* ~~and breakthrough~~__<span><b</span><span>r></span>
</pre>

__bold__<br>
**bold**<br> <!--ctrl+b with extension-->
<b>bold</b><br>
_italic_<br>
*italic*<br> <!--ctrl+i with extension-->
<i>italic</i><br>
<u>underline</u><br>
~~breakthrough~~<br> <!--alt+s on windows-->
__bold and *italic* ~~and breakthrough~~__<br>

#### [6단계] `인용구`: 인용할 경우 or 분위기 전환시 사용 (중첩 가능)
<pre>
> 위키백과?
> >e
> 
> e

>> 중대장 드립 검색
>>
>>
>>
>>
>>
>>
>>> "오늘 중대장은 너희에게 실망했다"
</pre>

> 위키백과?
> >e
> 
> e

>> 중대장 드립 검색
>>
>>
>>
>>
>>
>>
>>> "오늘 중대장은 너희에게 실망했다"

#### [7단계] 링크(Link) : 클릭하면 다른 페이지, 다른 부분으로 이동 가능

<pre>유형1(`설명어`를 클릭하면 URL로 이동) : [TheoryDB 블로그](https://theorydb.github.io "마우스를 올려놓으면 말풍선이 나옵니다.")<<span>/b><b</span><span>r></span>
유형2(URL 보여주고 `자동연결`) : <https://theorydb.github.io><<span>/b><b</span><span>r></span>
유형3(동일 파일 내 `id로 문단 이동`) :

<<span>a id = "markdown의-반드시-알아야-하는-문법">nyong</</span><span>a></span>

...

[동일 파일 내 `id로 문단 이동`](#markdown의-반드시-알아야-하는-문법 "처음으로 이동한다!")<<span>/b><b</span><span>r></span>

이건 pre tag로 작성한 것이다!!</pre>

유형1(`설명어`를 클릭하면 URL로 이동) : [TheoryDB 블로그](https://theorydb.github.io "마우스를 올려놓으면 말풍선이 나옵니다.")<br>
유형2(URL 보여주고 `자동연결`) : <https://theorydb.github.io><br>
유형3(동일 파일 내 `id로 문단 이동`) : [동일파일 내 문단 이동](#markdown의-반드시-알아야-하는-문법 "처음으로 이동한다!")

#### [8단계] 이미지(Image) : 이미지 보여주기

<pre>유형1(`이미지` 삽입) :  
![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png "인공지능")
  
유형2(`사이즈를 조절`하고 싶은 경우 HTML 태그로 처리) :   
< img src="https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png" width="300" height="200">
< !--편의상 앞에 띄어쓰기를 했당 안하면 출력되더라-->

유형3(이미지 삽입 후, `링크 걸기`)
[![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png)](https://theorydb.github.io/think/2019/06/25/think-future-ai/)</pre>

유형1(`이미지` 삽입) :  
![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png "인공지능")
  
유형2(`사이즈를 조절`하고 싶은 경우 HTML 태그로 처리) :   
<img src="https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png" width="300" height="200">

유형3(이미지 삽입 후, `링크 걸기`)
[![이미지](https://theorydb.github.io/assets/img/think/2019-06-25-think-future-ai-1.png)](https://theorydb.github.io/think/2019/06/25/think-future-ai/)

#### [9단계] 내가 추가한 단계
  1. 주석
  2. `` 넣기
  3. pre 태그
  4. span 태그
  5. 

### Markdown 문법2(유용한 부가기능)
### 실전연습
### 이미지를 쉽게 업로드 하는 방법
### 소소한 Tip 그리고 고장났을 때


