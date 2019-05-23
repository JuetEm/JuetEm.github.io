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
    - jekyll
    - blog
comments: true
---

**Jekyll Blog 에 Category를 추가해보자!!**

기존에 [Category Deploy](https://juetem.github.io/Category-Deploy/) 라는 글을 작성하면서 몇몇 블로그를 참고하여 카테고리 적용을 시도하였지만 <strong>실패!!</strong> 하였습니다.  

참고한 자료들에 문제가 있었던 것이 아니라, Jekyll과 템플릿 언어에 대한 이해가 부족했습니다.   

적어도!! 

**템플릿 언어**에 대한 기본적인 이해와 Jekyll 블로그가 가지고 있는 **변수**의 내용과 사용방법에 대한 개념 정도는 필요했습니다.

<u>위 두 내용에 대해서는 <i><strong>간단히 각 개념만 살짝</strong></i> 건드리고 각각에 대한 포스트는 따로 작성해보도록 하겠습니다.</u>

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

[Jekyll 공식 홈페이지 변수 설명 페이지의 링크][지킬 변수]에서 자세한 내용 확인 하실 수 있으니, 한 번 둘러보시길 권해드립니다.

## **2. Category 추가하기!**

- #### **개요**
<a href="#카테고리-추가-방식">2.0 카테고리 추가 방식</a>  
<a href="#config-편집">2.1 _config.yml 편집</a>  
<a href="#fron-matter에-categories-추가">2.2 post파일 front matter에 categories 추가</a>  
2.3 카테고리 폴더 및 index.html 생성  


- <h4 id="카테고리-추가-방식"><strong>2.0 카테고리 추가 방식</strong></h4>

> \- 단순한 방식으로 카테고리를 추가 하였습니다. <br> - 블로그 기본 페이지 상단에 위치한 네비게이션 바에 카테고리 매뉴를 추가합니다. <br> - 카테고리 매뉴를 클릭하면 Category 별 post 목록이 뿌려지는 화면으로 이동합니다.<br> - 카테고리 화면에서 포스트의 제목을 누르면 해당 포스트로 이동하여 포스트를 읽어볼 수 있습니다.


- <h4 id="config-편집"><strong>2.1 _config.yml 편집</strong></h4>

Jekyll 은 테마를 선택해서 쉽게 적용할 수 있다는 장점이 있습니다.  

`Jekyll Themes`  [jekyllthemes.org](jekyllthemes.org)  

이 블로그는 [kiko-now][키코 나우 페이지]라는 테마 템플렛을 커스터마아징 해서 사용하려고 합니다.  
이 테마에는 기본적으로 네비게이션 바가 적용되어 있습니다.  
`_config.yml` 파일의 navigation 설정부에 카테고리 관련 설정을 추가해주면 바로 카테고리가 네비게이션 바에 생겨나게 됩니다.

```
name: Category
url: /category
```

> ![_config.yml - nav 설정 영역에 category 추가]({{ site.baseurl }}/images/nav_add_category_edit.png)

`_config.yml` 파일에 설정 된 변수명들과 설정 방식이 조금 다르니 navigation 관련 설정부를 잘 찾아보세요.  
<u>navigation 이 애초에 존재하지 않으면 적용 방법을 찾아보거나, 다른 방식으로 카테고리를 적용 하셔야 합니다.</u>
 
 
- <h4 id="fron-matter에-categories-추가"><strong>2.2 post파일 front matter에 categories 추가</strong></h4>

`_posts` 폴더 안에 들어있는 md 혹은 markdown 확장자의 포스트 작성 파일의 맨위 front matter 부분에 카테고리 관련 설정을 해줍니다.
 
```
categories:
    - Customizing Jekyll Blog(카테고리명)
```
 
> ![post front matter에 categories: 카테고리 추가]({{site.baseurl}}/images/post_front_matter_category_edit.png)
 
post에 설정한 front matter의 변수를 site 전역변수로 읽어서 다음 화면에 뿌려주게 된답니다.



-----------------------------
**References**
1. [Category 적용 - Webjeda 블로그][웹제다 외국 블로그]
2. [Django 템플릿 언어 이해 - 잉고래님의 블로그][템플릿 언어]
3. [Jekyll 변수 - Jekyll 한국어 공식 홈페이지][지킬 변수]

[키코 나우 페이지]: https://aweekj.github.io/kiko-now/ 
[웹제다 외국 블로그]: https://blog.webjeda.com/jekyll-categories/
[템플릿 언어]: https://ingorae.tistory.com/401 
[지킬 변수]: https://jekyllrb-ko.github.io/docs/variables/ 