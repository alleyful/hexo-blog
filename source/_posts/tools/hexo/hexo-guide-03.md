---
title: HEXO - 검색 엔진 최적화(SEO)
toc: true
thumbnail: images/gallery/thumbnails/hexo.jpg
categories:
  - Tools
  - Hexo
tags:
  - Hexo
  - github.io
  - blog
  - seo
date: 2019-08-10 10:20:22
---

## 검색 엔진 최적화(SEO)
블로그 생성 후 내가 작성한 포스트가 검색에 노출되기 위해서는 검색엔진에 노출 될 수 있도록 검색 엔진 최적화 작업을 진행해 주어야 합니다.

{% blockquote 위키백과, 검색 엔진 최적화 %}
`검색 엔진 최적화(search engine optimization, SEO)`는 웹 페이지 검색엔진이 자료를 수집하고 순위를 매기는 방식에 맞게 웹 페이지를 구성해서 검색 결과의 상위에 나올 수 있도록 하는 작업을 말한다. 웹 페이지와 관련된 검색어로 검색한 검색 결과 상위에 나오게 된다면 방문 트래픽이 늘어나기 때문에 효과적인 인터넷 마케팅 방법 중의 하나라고 할 수 있다. 기본적인 작업 방식은 특정한 검색어를 웹 페이지에 적절하게 배치하고 다른 웹 페이지에서 링크가 많이 연결되도록 하는 것이다. 구글 등장 이후 검색 엔진들이 콘텐츠의 신뢰도를 파악하는 기초적인 지표로 다른 웹사이트에 얼마나 인용되었나를 사용하기 때문에 타 사이트에 인용되는 횟수를 늘리는 방향으로 최적화 한다.
{% endblockquote %}

<br/>
<br/>
<!-- more -->

## 검색엔진 최적화(SEO)에 유용한 플러그인 설치하기
HEXO에서는 SEO와 관련된 다양한 플로그인들이 있으며 그 중 몇 가지를 이용할 수 있도록 정리해 보겠습니다.

- hexo-auto-canonical
- hexo-generator-robotstxt
- hexo-autonofollow
- hexo-generator-feed
- hexo-generator-seo-friendly-sitemap

<br/>
<br/>

### hexo-auto-canonical
- 대표 URL(표준 링크)을 자동으로 생성해주는 플러그인입니다. 
- 설치   
	{% gdemo_terminal 'npm install --save hexo-auto-canonical' '70px' 'zsh' '500' '$' 'demo-teriminal-1' %}
	{% endgdemo_terminal %} 
	
<br/>
	
- 사용
	- 설치한 테마 내 HEAD 태그 내 삽입해서 사용합니다.
	
	- icarus의 경우에는 themes > icarus > layout > common > head 파일 내 `<%- meta(page) %>` 아래에 다음 코드를 넣어줍니다.  

	```html
//.ejs
<%- autoCanonical(config, page) %>

//.jade
| !{ autoCanonical(config, page) }
	```
	{% codeblock head.ejs %}
		<%- meta(page) %>
  <%- autoCanonical(config, page) %>
{% endcodeblock %}
  
<br/>
<br/>

### hexo-generator-robotstxt
- 자동으로 robot.txt 파일을 생성해주는 플러그인 입니다.
{% blockquote 위키백과, 로봇 배제 표준 %}
로봇 배제 표준은 웹 사이트에 로봇이 접근하는 것을 방지하기 위한 규약으로, 일반적으로 접근 제한에 대한 설명을 robots.txt에 기술한다. 이 규약은 권고안이며, 로봇이 robots.txt 파일을 읽고 접근을 중지하는 것을 목적으로 한다. 따라서, 접근 방지 설정을 하였다고 해도, 다른 사람들이 그 파일에 접근할 수 있다. robots.txt 파일은 항상 사이트의 루트 디렉토리에 위치해야 한다.
{% endblockquote %}

- 설치
	{% gdemo_terminal 'npm install hexo-generator-robotstxt --save' '70px' 'zsh' '500' '$' 'demo-teriminal-4' %}
  {% endgdemo_terminal %} 
  
  <br/>
  
- 사용
	{% codeblock _config.yml %}
    robotstxt:
      useragent: "*"
      allow:
        - /
      sitemap: https://username.github.io/sitemap.xml
  {% endcodeblock %}

<br/>
<br/>

### hexo-autonofollow
- 외부 링크에 `rel="external nofollow` 속성을 자동으로 추가해주는 기능을 하는 플러그인입니다.

- 설치
	{% gdemo_terminal 'npm install hexo-autonofollow --save' '70px' 'zsh' '500' '$' 'demo-teriminal-2' %}
  {% endgdemo_terminal %} 
  
  <br/>
  
- 사용
	{% codeblock _config.yml %}
    nofollow:
        enable: true
        exclude:
        - exclude1.com
        - exclude2.com
  {% endcodeblock %}
 
	| 옵션 | 내용 |
	|:---:|:---:|
	| enable | 플러그인 활성화 여부 (true, false) |
	| exclude | 제외시킬 host |

<br/>
<br/>

### hexo-generator-feed
- 자동으로 RSS feed를 생성해주는 플러그인 입니다.  
{% blockquote RSS Feed %}
어떤 사이트가 있을 때, 그 사이트를 매일 방문해서 재미있는 새로운 기사가 있는지 확인하는 것은 번거롭습니다. 특히 새 기사가 매일 또는 정기적으로 올라오는 것이 아니라 불규칙할 때는 더욱 그렇습니다.
그 사이트를 직접 방문하지 않고, 새 기사들만 자신의 컴퓨터로 "배달"이 된다면 편리할 것입니다.
RSS(Really Simple Syndication 의 약자) 같은 "사이트 피드"란, 새 기사들의 제목만, 또는 새 기사들 전체를 뽑아서 하나의 파일로 만들어 놓은 것입니다.
이제 각 사이트들에서 제공하는 RSS파일 주소만 수집하여 확인하면, 자신의 취향에 맞는 새로운 읽을거리를 쉽게 찾아서 읽을 수 있습니다.
그러나 모든 사이트에서 RSS피드를 제공하는 것은 아닙니다. 1년 내내 새로운 내용이 없는 정적인 사이트에서는 제공하지 않는 것이 보통입니다. 새로운 읽을거리가 자주 올라오는 "뉴스형", "블로그형" 사이트에서 주로 제공됩니다.
{% endblockquote %}

- 설치
	{% gdemo_terminal 'npm install hexo-generator-feed --save' '70px' 'zsh' '500' '$' 'demo-teriminal-3' %}
  {% endgdemo_terminal %} 
  
  <br/>
  
- 사용
	{% codeblock _config.yml %}
    feed:
      type: rss2
      path: rss2.xml
      limit: 20
  {% endcodeblock %}
 
	| 옵션 | 내용 |
	|:---:|:---:|
	| type | feed의 종류 (atom/rss2) - * 네이버는 atom을 지원하지 않음 |
	| path | feed가 생성될 경로(default : atom.xml, rss2.xml) |
	| limit | 최신 포스트 수 설정 (0 또는 false - 전체 포스트) |

<br/>
<br/>

### hexo-generator-seo-friendly-sitemap
- 크롤러가 블로그를 더욱 효율적으로 클롤링 할 수 있도록 사이트맵 xml 파일을 자동으로 생생해 줍니다.
- 설치
	{% gdemo_terminal 'npm install hexo-generator-seo-friendly-sitemap --save' '70px' 'zsh' '500' '$' 'demo-teriminal-5' %}
  {% endgdemo_terminal %} 
  
  <br/>
  
- 사용
	{% codeblock _config.yml %}
    sitemap:
      path: sitemap.xml
      tag: false
      category: false
  {% endcodeblock %}
  
  | 옵션 | 내용 |
  |:---:|:---:|
  | type | sitemap이 생성될 경로 |
  | path | sitemap에 tag 포함 여부 |
  | limit | sitemap에 category 포함 여부 |

<br/>
<br/>



## 검색엔진 등록하기

### 구글
- [구글 애널리틱스](https://accounts.google.com)(Google Analytic)
	- 가입 후 사이트 이름과 URL 등을 입력하고 추적 ID를 발급 받습니다. 이 아이디는 themes의 `_config.yml` 내 `google_analytics`에 넣어 줍니다.
	- 사용
	{% codeblock _config.yml %}
    plugins:
        google-analytics:
            # Google Analytics tracking id
            tracking_id: UA-*********-1
  {% endcodeblock %}
	
	<br/>
	
- [google search console](https://search.google.com/search-console) 
	- 구글 웹 마스터 도구가 Search Console로 변경되었습니다. 가입 후 속성을 추가해 줍니다. 생성된 html파일을 루트에 올린 후 확인 하는 방법과 애널리스틱 가입을 확인하는 방법으로 인증을 하는데, 저는 전자로 인증을 했습니다.
	
	- Sitemaps 메뉴에 위에서 생성한 `sitemap.xml`과 `rss2.xml`을 추가해 주세요.  
	![](/images/tools/search-console-sitemap.png)  
	
	- 사이드 등록 후 확인하기까지 시간이 걸릴 수 있습니다. Search Console에서 해당 사이트의 데이터를 수집 후 처리하는데 시간이 좀 걸리는 것 같습니다. 보통 2~3일 정도 예싱을 해야하며, 제 블로그 같은 경우 주말 포함 약 5일 정도의 시간이 지난 후 확인 할 수 있었습니다. 

<br/>
<br/>

### 네이버
- [NAVER 웹마스터도구](https://webmastertool.naver.com/)

	- 네이버 웹마스터 도구 페이지에서 `사이트 간단 체크하기` 메뉴를 통해 현재 블로그의 최적화 상태를 알아볼 수 있습니다.  
	![](/images/tools/naver-webmaster-01.png)
	
	<br/>
	
	- 연동 사이트 목록 페이지 내 사이트 추가에 블로그 주소를 추가해 줍니다.  
	![](/images/tools/naver-webmaster-02.png)
	
	<br/>
	
	- 추가 된 블로그를 클릭 후 요청 메뉴 내 사이트맵 RSS를 제출해 줍니다.  
	![](/images/tools/naver-webmaster-03.png)
	
<br/>
<br/>

### 다음 
- [다음 검색 등록](https://register.search.daum.net) 
	- 다음 검색 등록에서 신규등을 하면 됩니다. 등록한 이메일 접수완료 메일을 받을 수 있습니다.  
	![](/images/tools/daum-search.png)
	
<br/>

---

<br/>

## Refenence
- https://iseongho.github.io/posts/hexo-seo/
- https://futurecreator.github.io/2016/06/23/search-engine-optimization-hexo-plugins/
- http://mwultong.blogspot.com/2007/10/rss-rss-feed.html