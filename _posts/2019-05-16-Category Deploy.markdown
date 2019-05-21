---
layout: post
title:  "Category Deploy"
date:   2019-05-16 10:30:34 +0900
categories:
    - Customizing Jekyll Blog
tags:
    - jekyll
    - category
    - blog
comments: true
---
카테고리를 만들자!!  

`Jekyll을 이용한 블로그 작성` 외에도 `Flutter를 이용한 어플리케이션 만들기`도 역시 블로그 작성의 큰 이유중 하나기 때문에!!  

또한 앞으로 다루고자 하는 블로그 글의 주제들이 점점 늘어날 것이기 때문에!!  

초기에는 존재하지 않았던 `Category` 매뉴를 만들어 보고자 합니다.

---

# 카테고리 만들기

*  _layout 폴더에 category.htlm 파일 생성


```html
---
layout:  default
---
<ul class="posts-list">{% raw %}
	{% assign category = page.category | default: page.title %}
	{% for post in site.categoryies[category] %}
	<li>
		<h3>
			<a href="{{ site.baseurl }}{{ post.url }}">
				{{ post.title }}
			</a>
			<small>{{ post.date | date_to_string }}</small>
		</h3>
	</li>
	{% endfor %}{% endraw %}
</ul>

```

* _includes 폴더 index.html 파일 수정

```html
<ul class="site-category">{% raw %}
		{% assign pages_list = site.pages %}
		{% for node in pages_lsit %}
			{% if node.title != null %}
				{% if node.layout == "category" %}
					<li>
						<a class="category-link {% if page.url == node.url %} active{% endif %} href="{{ site.baseurl }}{{ node.url }}">{{ node.title }}</a>
					</li>
				{% endif %}
			{% endif %}
		{% endfor %}{% endraw %}
</ul>
```

* category 폴더 생성

루트 디렉토리 폴더 안에 category 폴더를 만들어준 다음 원하는 카테고리 이름의 md(markdown) 파일을 생성

`마크다운파일.md` 파일 예시

```
layout: category

title: 마크다운파일 
```

* 블로그 포스트에 category 추가

위 세가지 셋팅 후 작성하는 포스트의 맨 위(front matter)에 `categories: 카테고리명`을 추가해 주면 된다.

# 그러나!!!! 동작하지 않는다!!! 왜?! 나는 바보 개발자이기 때문이다!!

- `jekyll의 변수들`에 대해서 이해하고 넘어가자! 

---
References  
[블로그 카테고리 만들기][블로그 카테로기 만들기]  
[HTML H, Head, Header 차이점][HTML H, Head, Header 차이점]


[블로그 카테로기 만들기]: https://devyurim.github.io/development%20environment/github%20blog/2018/08/07/blog-6.html
[HTML H, Head, Header 차이점]: https://dasima.xyz/html-heading-head-header/
