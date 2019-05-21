---
layout: post
title:  "Category Deploy - 드디어!!"
date:   2019-05-21 14:32:34 +0900
categories:
    - Customizing Jekyll Blog
tags:
    - category
    - customizing
    - tag
---

# **Jekyll Blog 에 Category를 추가해보자!!**

기존에 [Category Deploy](https://juetem.github.io/Category-Deploy/) 라는 글을 작성하면서 몇몇 블로그를 참고하여 카테고리 적용을 시도하였지만!! 실패를 하였습니다.  

참고한 자료들에 문제가 있었던 것이 아니라 제가 Jekyll과 템플릿 언어에 대한 이해가 부족해서 그런 것으로 밝혀졌습니다.   

적어도!! **템플릿 언어**에 대한 기본적인 이해와 Jekyll 블로그가 가지고 있는 **변수**의 내용과 사용방법에 대한 개념 정도는 필요했습니다.

<u><i><strong>간단히 각 개념만 살짝</strong></i> 건드리고 각각에 대한 포스트는 따로 작성해보도록 하겠습니다.</u>

이해가 급하신 분은 아래 **References**를 먼저 참고해주세요! 

## **1. 개념 간단히 잡기!**

- #### **템플릿 언어**

쉽게 말하면 
```
1. 템플릿 언어로 텍스트 파일을 작성하면, 
2. 해석해주는 엔진(Jekyll에서는 liquid 엔진)이 있어서, 
3. 규칙에 맞게 내용을 HTML로 변환 해준다
```
는 것으로 이해했습니다.

- #### **Jekyll 변수**

지금 포스트에서 사용하는 변수 위주로만 짚고 넘어가겠습니다.

변수 종류|변수 형태|설명(내용)
---|---|---
전역변수|`site`|사이트 정보 + `_config.yml`의 환경설정 정보
사이트 변수|`site.categories[CATEGORY]`|`CATEGORY` 카테고리에 속한 모든 포스트 목록
포스트 변수|`post in site.categories[CATEGORY]`|사이트 변수에서 특정 카테고리의 포스트를 할당한 포스트 변수
포스트 변수|`post.title`|Post의 Front Matter에 설정된 포스트의 제목(title)
포스트 변수|`post.date`|Post의 Front Matter에 설정된 포스트의 날짜(date)
---|---|---

## **2. Category 추가하기!**

- #### **개요**


-----------------------------
> **References**
>> 1. [Category 적용 - Webjeda 블로그][웹제다 외국 블로그]
>> 2. [Django 템플릿 언어 이해 - 잉고래님의 블로그][템플릿 언어]
>> 3. [Jekyll 변수 - Jekyll 한국어 공식 홈페이지][지킬 변수]

[웹제다 외국 블로그]: https://blog.webjeda.com/jekyll-categories/
[템플릿 언어]: https://ingorae.tistory.com/401 
[지킬 변수]: https://jekyllrb-ko.github.io/docs/variables/ 