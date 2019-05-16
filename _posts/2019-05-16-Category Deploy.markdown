---
layout: post
title:  "Category Deploy"
date:   2019-05-16 10:30:34 +0900
categories: jekyll update
---
`Jekyll을 이용한 블로그 작성` 외에도 `Flutter를 이용한 어플리케이션 만들기`도 역시 블로그 작성의 큰 이유중 하나기 때문에!!  

또한 앞으로 다루고자 하는 블로그 글의 주제들이 점점 늘어날 것이기 때문에!!  

초기에는 존재하지 않았던 `Category` 매뉴를 만들어 보고자 합니다.

---

# 카테고리 만들기

1. _layout 폴더에 category.htlm 파일 생성


```html
---
layout:  default
---
<ul class="posts-list">
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
	{% endfor %}
</ul>

```

2. _includes 폴더 index.html 파일 수정

---
References  
[블로그 카테고리 만들기][블로그 카테로기 만들기]  
[HTML H, Head, Header 차이점][HTML H, Head, Header 차이점]


[블로그 카테로기 만들기]: https://devyurim.github.io/development%20environment/github%20blog/2018/08/07/blog-6.html
[HTML H, Head, Header 차이점]: https://dasima.xyz/html-heading-head-header/
