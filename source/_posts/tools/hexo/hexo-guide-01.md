---
title: HEXO - 시작하기
toc: true
thumbnail: images/gallery/thumbnails/hexo.jpg
categories:
  - Tools
  - Hexo
tags:
  - Hexo
  - github.io
  - blog
date: 2019-07-07 20:28:44
---

## 정적 블로그, HEXO 시작해보기
프론트엔트 개발을 시작하면서 그동안 공부해오던 것을 정리해야할 필요성이 생겼습니다. 
좋은 자료, 세미나, 기술 서적, 스터디, 개발하면서 느꼈던 점 등을 정리하고 그 흔적을 남겨보고자 블로그를 시작하게 되었습니다. 

설치형 블로그, 서비스형 블로그, 동적 혹은 정적 블로그 등 설치 방법과 사용방법에 따라 다양하게 나뉘고 있는 블로그들 중 설치형 정적 블로그로 말할 수 있는 `HEXO`를 사용하게 되었고, 그 방법을 공유하고자 합니다.

<br/>
<!-- more -->

### 공식 사이트에서 얘기하는 HEXO!
 Node.js 기반의 정적사이트 생성기(Static site generator)의 일종으로 `빠르고 간단하고 강력한 블로그 프레임워크`입니다.
 

1.  `엄청나게 빠른 속도`  
	- Node.js는 몇 초만에 수백개의 파일을 빌드할 수 있을 정도로 빠른 생성 속도를 제공합니다.
	
2.  `Markdown 지원`  
	- 친화적인 Markdown의 모든 기능을 지원하며 거의 모든 Octopress 플러그인들을 사용할 수 있습니다.
	
3.  `한 번의 명령으로 Deployment 하기`  
	- 단지 하나의 명령어로 당신의 웹 사이트를 GitHub나 Heroku에 deploy할 수 있습니다.
	
4.  `다양한 플러그인`  
	- Hexo는 강력한 플러그인 시스템을 가지고 있습니다. 사용자는 Jade와 CoffeeScript를 위한 플러그인들을 설치할 수도 있습니다.

<br/>

---

<br/>

## 설치하기

### 설치전 확인
Git과 Node.js가 설치 되어 있어야 합니다. 설치되지 않았다면 아래 경로에서 확인해 주세요.

- [Node.js](https://nodejs.org/en/) - 6.9 이상  
- [Git](https://git-scm.com/)
	
<br/>





### HEXO INSTALL
- [Hexo](https://hexo.io/ko/docs/setup) 공식 사이트에 간단한 설치방법과 사용법이 나와있습니다. 

	{% gdemo_terminal 'npm install -g hexo-cli' '70px' 'zsh' '500' '$' 'demo-teriminal1' %}
	{% endgdemo_terminal %}
	
	- hexo-cli를 global로 설치해주세요.

	<br/>

### HEXO INIT
- hexo를 설치할 폴더에 `init으로 기본 파일을 생성`해 주세요.

	{% gdemo_terminal 'hexo init <folder>' '70px' 'zsh' '500' '$' 'demo-teriminal2-1' %}
	{% endgdemo_terminal %}  <br/>
	
	{% gdemo_terminal 'cd <folder>' '70px' 'zsh' '500' '$' 'demo-teriminal2-2' %}
  {% endgdemo_terminal %}  <br/>

	{% gdemo_terminal 'npm install' '70px' 'zsh' '500' '$' 'demo-teriminal2-3' %}
  {% endgdemo_terminal %}
  
	- 기본 설정이 된 폴더로 이동을 한 후 npm install을 해주세요.
	- 초기화가 완료되었다면 아래와 같은 폴더구조를 확인 할 수 있습니다.
	
	```
	.
	├── _config.yml
	├── package.json
	├── scaffolds
	├── source
	|   ├── _drafts
	|   └── _posts
	└── themes
	```

<br/>
	

### HEXO SERVER
- `hexo server` 또는 `hexo s`를 명령어를 사용하여 로컬 서버에서 블로그를 확인 할 수 있습니다.
	{% gdemo_terminal 'hexo server' '70px' 'zsh' '500' '$' 'demo-teriminal3' %}
	{% endgdemo_terminal %}

	- localhost:4000 에서 확인 할 수 있습니다.

<br/>

---

<br/>



## 글쓰기  

### 새글 작성   
- `hexo new [layout] <title>` 사용하여 새글 작성을 할 수 있습니다.


{% gdemo_terminal 'hexo new test.md' '70px' 'zsh' '500' '$' 'demo-teriminal4' %}
{% endgdemo_terminal %}

- 명령어를 사용하면 `/scaffolds/`의 md 파일을 스캐폴딩 합니다.
- 발행되지 않는 형태의 초안 문서를 작성하고 싶은 경우 [layout]에 draft를 사용해 줍니다.
- 아래와 같은 경로에 markdown 문서가 만들어 집니다.

```terminal
.
└── source
   ├── _drafts
   └── _posts
      └── test.md
```  

<br/>

### Front-matter
- 생성된 test.md에서 `타이틀` 및 `발행시간`, `카테고리`, `테마` 등을 수정할 수 있습니다.

{% codeblock test.md %}
---
title: 첫번째 포스팅입니다.
categories:
- TOOL
- HEXO
tags:
- HEXO
- BLOG
date: 2019-07-06 22:15:19
---
{% endcodeblock %}

- [Front-matter](https://hexo.io/docs/front-matter.html)는 YAML 또는 JSON 형태로 작성할 수 있습니다.
- `[`, `:` ...등의 문자는 제목에 들어가면 오류가 날 수 있습니다. ""로 감싸서 사용해주세요.
	
<br/>

### Publish
- post에 바로 발행하지 않고 deaft문서를 작성했다면 publish를 이용해 발행해 줍니다.
{% gdemo_terminal 'hexo publish' '70px' 'zsh' '500' '$' 'demo-teriminal5' %}
{% endgdemo_terminal %}
	
<br/>

---

<br/>


## 배포하기(Deploy)

### 깃 저장소 확인
- 저장소 2개를 준비합니다.
	- 정적파일이 deploy되는 `(githubID).github.io`
	- hexo 블로그 및 md 파일을 관리할 수 있는 repository (ex. blog)

<br/>

### 환경설정
- _config.yml 파일을 수정해 주세요.
{% codeblock _config.yml %}
# URL
url: https://alleyful.github.io //(githubID).github.io
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Deployment
deploy:
  type: git
  repo: https://github.com/alleyful/alleyful.github.io.git //gihub pages repository
  branch : master
{% endcodeblock %}

<br/>

### hexo generate

{% gdemo_terminal 'hexo generate' '70px' 'zsh' '500' '$' 'demo-teriminal6' %}
{% endgdemo_terminal %}

- 정적파일을 생성해 public폴더에 넣어줍니다.

<br/>

### hexo deploy

1. deploy를 하기 위해서 `npm install hexo-deploy-git --save` 플러그인을 먼저 설치해 주세요.

{% gdemo_terminal 'hexo-deploy-git' '70px' 'zsh' '500' '$' 'demo-teriminal7' %}
{% endgdemo_terminal %}	<br/>

{% gdemo_terminal 'hexo deploy' '70px' 'zsh' '500' '$' 'demo-teriminal8' %}
{% endgdemo_terminal %}	

- 플러그인을 설치 한 후 deploy를 해줍니다. 
- Github Pages에서 확인 할 수 있습니다.
	- `https://<계정이름>.github.io`
	
<br/>

### hexo blog 버전관리
- 위에서 만들어 놓은 repository 중 blog(또는 원하는 이름의 저장소)를 사용해 주세요.

<br/>
<br/>


---

## 테마적용도 해볼까요.

HEXO를 설치하고 POST를 작성한 후 Git Pages에 Deploy까지 해 보았습니다.  
다음글에는 HEXO Theme를 사용하여 블로그에 원하는 layout과 스타일을 적용해 보도록 하겠습니다.

<br/>

