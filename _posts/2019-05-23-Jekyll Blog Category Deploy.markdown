---
layout: post
title:  "Category Deploy - 드디어!!"
date:   2019-05-23 16:28:41 +0900
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

Jekyll Blog 에 Category를 추가해보자!!

기존에 [Category Deploy](https://juetem.github.io/Category-Deploy/) 라는 글을 작성하면서 몇몇 블로그를 참고하여 카테고리 적용을 시도하였지만 <strong>실패!!</strong> 하였습니다.  

참고한 자료들에 문제가 있었던 것이 아니라, Jekyll과 템플릿 언어에 대한 이해가 부족했습니다.   

적어도!! 

**템플릿 언어**에 대한 기본적인 이해와 Jekyll 블로그가 가지고 있는 **변수**의 내용과 사용방법에 대한 개념 정도는 필요했습니다.

<u>위 두 내용에 대해서는 <i><strong>간단히 개념만 살짝</strong></i> 건드리고 각각에 대한 포스트는 따로 작성해보도록 하겠습니다.</u>

이해가 급하신 분은 아래 <a href="#references"><strong>References</strong></a>를 먼저 참고해주세요! 

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

이번 포스트에서 사용하는 변수 위주로만 짚고 넘어가겠습니다.

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
<a href="#카테고리-폴더-인덱스-생성">2.3 카테고리 폴더 및 index.html 생성</a>   


- <h4 id="카테고리-추가-방식"><strong>2.0 카테고리 추가 방식</strong></h4>

> \- 단순한 방식으로 카테고리를 추가 하였습니다. <br> - 블로그 기본 페이지 상단에 위치한 네비게이션 바에 카테고리 매뉴를 추가합니다. <br> - 카테고리 매뉴를 클릭하면 Category 별 post 목록이 뿌려지는 화면으로 이동합니다.<br> - 카테고리 화면에서 포스트의 제목을 누르면 해당 포스트로 이동하여 포스트를 읽어볼 수 있습니다.


- <h4 id="config-편집"><strong>2.1 _config.yml 편집</strong></h4>

Jekyll 은 테마를 선택해서 쉽게 적용할 수 있다는 장점이 있습니다.  

`Jekyll Themes` 주소 : [jekyllthemes.org][지킬테마]  

이 블로그는 [kiko-now][키코 나우 페이지]라는 테마 템플렛을 커스터마아징 해서 사용하려고 합니다.  

이 테마에는 기본적으로 네비게이션 바가 적용되어 있습니다.  

`_config.yml` 파일의 navigation 설정부에 카테고리 관련 설정을 추가해주면 바로 카테고리가 네비게이션 바에 생겨나게 됩니다.

```
name: Category
url: /category
```

> ![_config.yml - nav 설정 영역에 category 추가]({{ site.baseurl }}/images/nav_add_category_edit.png)

> ![navigation Bar 영역에 category 메뉴 추가]({{site.baseurl}}/images/generated category.png)

이제 네비게이션 바에서 `Category` 매뉴를 클릭하면 앞서 `_config.yml` 파일에 해당 이름(Category)의 `url` 경로로 설정해 둔 `/category`로 이동하게 됩니다. 

`_config.yml` 파일에 설정 된 변수명들과 설정 방식이 조금 다르니 navigation 관련 설정부를 잘 찾아보세요.  
<u>navigation 이 애초에 존재하지 않으면 적용 방법을 찾아보거나, 다른 방식으로 카테고리를 적용 하셔야 합니다.</u>
 
 
- <h4 id="fron-matter에-categories-추가"><strong>2.2 post파일 front matter에 categories 추가</strong></h4>

`_posts` 폴더 안에 들어있는 md 혹은 markdown 확장자의 포스트 작성 파일의 맨위 front matter 부분에 카테고리 관련 설정을 해줍니다.

**잠깐!! front matter 란?**
> `front matter` 란 Jekyll에서 포스트/페이지를 관리하는데 사용하는 YAML 방식의 문서의 헤더 양식입니다.

```
---
layout: post // post, page 중 하나를 넣어 이것이 한 페이지에 속하는 블로그 포스트인지, 홈페이지를 구성하는 하나의 큰 페이지인지를 결정합니다.
title: "제목" // 포스트나 피이지의 제목을 넣습니다.
date: 2019-05-20 11:28:22 +0900
modified: 2019-05-21 14:32:34 +0900
categories: 카테고리명 // 어느 카테고리에 속하는지 표시합니다.
excerpt: "요약문" // 페이지에 대한 요약문을 작성합니다.
tags: [태그명] // 해당 포스트의 태그를 지정해줍니다.
comments: true // 댓글 기능을 사용할지 결정합니다. 별도의 댓글 기능 적용 후에 사용 가능합니다.
---
```
> _참고자료 : [Uno's Blog][Front Matter]_

우리가 작성/추가 해야하는 카테고리 관련 front matter 설정 내용은 다음과 같습니다. 
 
```
categories:
    - Customizing Jekyll Blog(카테고리명)
```
 
> ![post front matter에 categories: 카테고리 추가]({{site.baseurl}}/images/post_front_matter_category_edit.png)
 
post에 설정한 front matter의 변수를 site 전역변수로 읽어서 카테고리 화면에 뿌려주게 된답니다.

**여기서 Tip!! categories 설정 방법** 

post의 front matter에 categories를 설정해주는 방법은 한 가지가 아닙니다.
(tags도 마찬가지입니다.)

앞서 작성한 `front matter란?` 의 에시와 그 아래에 `우리가 작성...다음과 같습니다.`의 categories 설정 방식이 서로 다른 것을 확인하셨을 텐데요.

일반적인 문서에서는 보통 다음과 같이 카테고리 추가 방법을 설명합니다.

__방식1__
```
---
categories: [category1, category2, category3]
---
```

제가 제시한 방식은 다음과 같습니다.

__방식2__
```
---
categories:
    - my post category1
    - my post category2
    - my post category3
---
```

차이점이 보이시나요?

`방식1`은 주로 하나의 단어로 category를 설정할 때 사용합니다. `방식2`는 카테고리의 이름이 여러 단어로 되어 있을 때 사용합니다.

`방식1`에서도 여러 단어의 카테고리명이 설정 가능한 경우도 있다고 하는데, 저는 전부 안되어서 `방식2`를 사용하고 있습니다. 여러 단어일 경우 단어들 사이의 공백을 `-(하이픈)` 등으로 이어서 사용하라고 하더군요.

__방식1-1__
```
---
categories: [my-post-category1, my-post-category2, my-post-category3]
---
```

여기까지 post 파일 front matter에 categories 설정이 되었다면, 이제는 템플릿 코드를 작성해서 블로그의 카테고리를 읽어볼 차례입니다.

- <h4 id="카테고리-폴더-인덱스-생성"><strong>2.3 카테고리 폴더 및 index.html 생성</strong></h4>

_config.yml 에 baseurl로 설정하신 경로에 category 폴더를 생성해줍니다.  

baseurl에 아무 값도 설정하지 않았다거나 `/`로 설정 했다면 블로그 프로젝트 폴더에 생성해주시면 됩니다. 

아래 사진처럼 (*언더바로 시작하는*) 기본적인 Jekyll 블로그 구성 요소 폴더들과 같은 경로에 생성해주세요.

> ![baseurl 경로에 category 폴더 생성]({{site.baseurl}}/images/category_folder_add.png)

블로그 프로젝트 디렉토리에 category 폴더를 생성하셨다면 이제 그 안에 `index.html` 파일을 만들어 줄 차례입니다.

```html
---
layout: page
permalink: /category/ <!-- /category/ 경로를 호출 했을 때 index.html이 호출 되도록 permalink 경로를 설정 해줍니다. -->
title: Category <!-- Category 화면의 제목으로 뿌려집니다. -->
---

{% raw %}
<div id="archives">
{% for category in site.categories %} <!-- site 전역변수 중 categories를 가져와서 반복해서 category에 할당해주세요!! -->
	<div class="archive">
		{% capture category_name %}{{ category | first }}{% endcapture %} <!-- 할당 받은 category 중 제일 첫번째 항목을 category_name에 담습니다. -->
		<div id="#{{ category_name | slugify }}"></div>
		<p></p>
		
		<h2 class="category-head">{{ category_name }}</h2> <!-- 불러온 카테고리 이름을 소제목으로 뿌려줍니다. -->
		<a name="{{ category_name | slugify }}"></a>
		{% for post in site.categories[category_name] %} <!-- site 전역 변수 내부에 해당 카테고리 이름을 가지고 있는 모든 post 들을 반복해서 post 객체에 할당해줍니다. -->
		<article class="archive">
			<a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> <!-- 포스트의 제목을 뿌려주고, 제목을 누르면 포스트로 이동 할 수 있도록 링크를 걸어줍니다. -->
			<time>{{ post.date | date: "%Y-%m-%d" }}</time> <!-- 포스트 작성 시간도 함께 보여줍니다. -->
		</article>
		{% endfor %}
	</div>
{% endfor %}
</div>
{% endraw %}
```

템플릿 언어도, HTML도 잘 모르는 터라 대충 코드 해석을 해보았습니다. 잘못된 부분 있으시면 말씀 주세요.

위와 같이 `index.html` 파일을 앞서 생성해 준 `category` 폴더에 위치시켜 주면, 메인화면 네비게이션 바의 `Category` 매뉴를 클릭 했을 때 다음과 같은 화면을 확인 하실 수 있습니다.

> ![카테고리 적용 화면]({{site.baseurl}}/images/Category Index Page.png)

물론 다음 화면처럼 카테고리별 포스트의 목록이 뿌려지기 위해서는, 다양한 카테고리의 여러개의 포스트가 해당 블로그에 있어야 겠지요?!

테스트 포스트들을 여러개 만들어서 확인해보세요.

## **마치며**

단순한 카테고리 메뉴에 index 화면 하나 뿌려주는데도 저는 많이 고생했습니다.

이번 포스트의 방식 외에도 다양한 그리고 더 고급진 방법들이 여럿 있는것 같더라구요.

좋은 방법 있으시면 공유 부탁드립니다!

앞으로의 커스터마이징_(방문자 수, 드롭다운 매뉴, 배경 이미지 등등)_ 과정도 공유 하겠습니다. 

감사합니다.

-----------------------------
<h2><strong id="references">References</strong></h2>
1. [Category 적용 - Webjeda 블로그][웹제다 외국 블로그]
2. [Django 템플릿 언어 이해 - 잉고래님의 블로그][템플릿 언어]
3. [Jekyll 변수 - Jekyll 한국어 공식 홈페이지][지킬 변수]
4. [Jekyll Front Matter 및 다수 - Uno's Blog][Front Matter]
5. [Category 설정 방식의 차이 - Nolboo's Blog][카테고리 설정]

[키코 나우 페이지]: https://aweekj.github.io/kiko-now/ 
[웹제다 외국 블로그]: https://blog.webjeda.com/jekyll-categories/
[템플릿 언어]: https://ingorae.tistory.com/401 
[지킬 변수]: https://jekyllrb-ko.github.io/docs/variables/ 
[Front Matter]: https://djkeh.github.io/articles/Hangul-test-jekyll-tips-kor/ 
[카테고리 설정]: https://nolboo.kim/blog/2014/01/09/upgrade-jekyll-github-blog/#%ED%83%9C%EA%B7%B8%EC%99%80-%EC%B9%B4%ED%85%8C%EA%B3%A0%EB%A6%AC 
[지킬테마]: jekyllthemes.org