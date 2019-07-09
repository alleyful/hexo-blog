---
title: HEXO - THEME(ICARUS)
toc: true
thumbnail: images/gallery/thumbnails/hexo.jpg
categories:
  - Tools
  - Hexo
tags:
  - Hexo
  - github.io
  - blog
date: 2019-07-09 23:38:37
---

## HEXO 테마 설치하기
hexo를 설치하면 기본적으로 `landscape` 테마가 설치되어 있습니다. 
하지만 직접 테마를 만들어 쓸 수 있도록 가이드를 제공하고 있습니다.
기본 설정을 수정해서 직접 테마를 만들어 사용하고 싶으시다면 [HEXO THEME](https://hexo.io/ko/docs/themes.html)를 확인 해 주세요.

<br/>
<!-- more -->


### 테마찾기
기본 테마보다 이미 만들어진 다양한 스타일의 테마를 찾고 싶다면 [Themes](https://hexo.io/themes/index.html)에서 찾을 수 있습니다.  
저는 ICARUS 테마를 설치하였습니다. 설치방법 및 사용방법은 비슷하기 문에 테마들 중 원하는 테마가 있는지 찾아보시기 바랍니다.

- [ICARUS GITHUB](https://github.com/ppoffice/hexo-theme-icarus) 
- [블로그 미리보기](https://blog.zhangruipeng.me/hexo-theme-icarus/)

<br/>

### 설치하기

- hexo init을 했던 폴더로 이동해서 clone 해주세요.
	{% gdemo_terminal 'git clone https://github.com/ppoffice/hexo-theme-icarus.git themes/icarus -b' '70px' 'zsh' '500' '$' 'demo-teriminal-1' %}
	{% endgdemo_terminal %}  
	
	
<br/>

### 환경설정

- hexo의 `_config.yml`의 `THEME`를 기본이었던 landscape에서 icarus로 수정해주세요.

	{% codeblock _config.yml %}
	## Themes: https://hexo.io/themes/
	theme: icarus
	{% endcodeblock %}
	
	- icarus의 기본 테마 설치가 끝났습니다.
	- `hexo s`로 로컬서버에서 확인 할 수 있습니다.
	
<br/>

- Profile Sidebar Widget

	{% codeblock _config.yml %}
    -
      type: profile
      position: # show in left or right sidebar
      author: # your name
      author_title: # your title
      location: # where are you
      avatar: # path or url to your avatar image
      gravatar: # your gravatar email
      follow_link: # path or url to any page you want
      social_links: # add links to your social network here
  {% endcodeblock %}
    
    - profile 설정을 할 수 있습니다.
  
<br/>

- Sidebar Widgets Overview
	{% codeblock _config.yml %}
    widgets:
        -
            type: category
            position: left
        -
            type: tagcloud
            position: left
        -
            type: recent_posts
            position: right
        -
            type: archive
            position: right
        -
            type: tag
            position: right
  {% endcodeblock %}
  
  - 위젯의 위치를 설정할 수 있습니다.
  - 왼쪽과 오른쪽으로 나눌 수 있으며, 한쪽으로 정렬할 경우 제 블로그처럼 컨텐츠 영역을 더욱 넢게 사용 할 수 있습니다.

<br/>

- Make a Sidebar Sticky When Page Scrolls

	{% codeblock _config.yml %}
  sidebar:
      left:
          sticky: false
      right:
          sticky: true
  {% endcodeblock %}
  
  - 양쪽 위젯의 position sticky 값을 설정할 수 있습니다.
  - true : top 고
  
<br/>
<br/>

---


## 활용

### Thumbnail
- thumbnail의 사용 유무를 설정 할 수 있습니다.

	- _config.yml
	{% codeblock _config.yml %}
	article:
      thumbnail: true
	{% endcodeblock %}  
	
	- post의 front-matter
	{% codeblock post.md %}
  title: Getting Started with Icarus
  thumbnail: /gallery/thumbnails/desert.jpg
  ---
  내용
  {% endcodeblock %}
  
<br/>
 
### Table of Contents / Catalogue
- Post 내 컨텐츠의 목차를 보여줄 수 있습니다. 오른쪽에 보이는 `CATALOGUE`의 형태로 보여집니다.

	- post의 front-matter
  {% codeblock post.md %}
  title: Table of Contents Example
  toc: true
  ---
  내용
  {% endcodeblock %}
    
	- _config.yml
	{% codeblock _config.yml %}
	widgets:
      -
          type: toc
          position: left
	{% endcodeblock %}  
	
<br/>

### Block Quote
- blockquote 타입의 컨텐츠를 보여줄 수 있습니다.

	- No arguments
	```javascript
	{% blockquote %}
 Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
 {% endblockquote %}
	```
	<br/>

	{% blockquote %}
	Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
	{% endblockquote %}
	
	<br/>
	
	- Quote from an article on the web
  ```javascript
  {% blockquote Seth Godin https://alleyful.github.io/2019/07/07/tools/hexo/hexo-guide-01/ HEXO - 시작하기 %}
  HEXO - 시작하기
  {% endblockquote %}
  ```
	<br/>

	{% blockquote Seth Godin https://alleyful.github.io/2019/07/07/tools/hexo/hexo-guide-01/ HEXO - 시작하기 %}
	HEXO - 시작하기
	{% endblockquote %}
  
  <br/>
  
### Code Block
- code형태의 컨텐츠를 보여줄 수 있습니다.

	- 기본형태
	```javascript
	{% codeblock [title] [lang:language] [url] [link text] %}
 code snippet
 {% endcodeblock %}
	```

	<br/>
	
	- Adding a caption to the code block
	
	```javascript
	{% codeblock Array.map %}
  array.map(callback[, thisArg])
  {% endcodeblock %}
	```
	<br/>
	
	{% codeblock Array.map %}
	array.map(callback[, thisArg])
	{% endcodeblock %}
	
	<br/>
	
	- Adding a caption and a URL
	
	```javascript
  {% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
  _.compact([0, 1, false, 2, '', 3]);
  => [1, 2, 3]
  {% endcodeblock %}
  ```
	<br/>
  
	{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
	_.compact([0, 1, false, 2, '', 3]);
	=> [1, 2, 3]
	{% endcodeblock %}
	
<br/>

### ETC.

- Pull Quote
- jsFiddle
- Gist
- iframe
- Image
- Link
- YouTube
- Vimeo

등 많은 helper 들의 사용법을 [여기](https://blog.zhangruipeng.me/hexo-theme-icarus/Configuration/Posts/hexo-built-in-tag-helpers/)에서 확인 할 수 있습니다.

<br/>
<br/>

---

## HEXO BLOG 검색 엔진 최적화(SEO)
내가 만든 블로그가 검색 될 수 있도록 해보도록 할까요?
다음글에서는 HEXO BLOG의 검색 최적화에 도전해 보도록 하겠습니다.

<br/>