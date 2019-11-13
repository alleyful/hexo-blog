---
title: NOMADCODERS Youtube Challenge - Day4 of 42
thumbnail: images/gallery/thumbnails/youtubeChallenge.jpg
categories:
  - develop
  - log
  - youtube-challenge
tags:
  - ES6
  - challenge
  - nomadcoders
  - 노마드코더
  - 챌린지
  - NodeJS
  - Pug
  - MongoDB
date: 2019-09-27 12:32:19
---



> Today's challenge is based on videos #2.3 to #2.7

- 오늘 시청하는 강의: #2.3 to #2.7
- 오늘 제출하는 과제: 위의 강의를 시청하신 후, 아래 코딩챌린지를 완료하세요.

<br/>

[[노마드 코더] 유튜브 클론 코딩](https://academy.nomadcoders.co/courses/enrolled/435438)

`#2 ExpressJS`
- 2.3 Your First Express Server 
- 2.4 Handling Routes with Express 
- 2.5 ES6 on NodeJS using Babel 
- 2.6 Express Core: Middlewares 
- 2.7 Express Core: Middlewares part Two 

<br/>
<!-- more -->

---

<br/>

## Lecture Summery

### Express

#### 설치
```
npm install express --save
```

<br/>

#### Routing
```js
var express = require('express');
var app = express();

// respond with "hello world" when a GET request is made to the homepage
app.get('/', function(req, res) {
  res.send('hello world');
});
```

<br/>

#### Route Methods
```js
// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage');
});

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage');
});

//모든 요청 메소드에 대해 한 경로에서 미들웨어 함수를 로드하는 데 사용
app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...');
  next(); // pass control to the next handler
});
```

<br/>

### Babel
Babel은 ES6+ 코드를 ES5 이하의 버전으로 트랜스파일링한다.

```js
// ES6(Arrow Function) + ES7(Exponentiation operator)
[1, 2, 3].map(n => n ** n);
```
위 코드는 ES6에서 도입된 화살표 함수와 ES7에서 도입된 거듭제곱 연산자를 사용하고 있다. 이 두가지 기능은 IE는 물론이고 구형 브라우저에서 지원하지 않는다. 따라서 IE나 구형 브라우저에서도 동작하는 애플리케이션을 구현하기 위해 ES6+ 코드를 ES5 이하의 버전으로 변환(트랜스파일링)할 필요가 있다. Babel을 사용하면 위 코드를 아래와 같이 ES5 이하의 버전으로 트랜스파일링할 수 있다.

```js
// ES5
"use strict";

[1, 2, 3].map(function (n) {
  return Math.pow(n, n);
});
```

<br/>

#### Babel CLI 설치
npm을 사용하여 Babel CLI을 설치한다.
```
# 프로젝트 폴더 생성
$ mkdir es6-project && cd es6-project

# package.json 생성
$ npm init -y

# babel-core, babel-cli 설치
$ npm install --save-dev @babel/core @babel/cli
```

#### babelrc 설정파일
Babel을 사용하려면 먼저 @babel/preset-env을 설치해야 한다. @babel/preset-env은 함께 사용되어야 하는 Babel 플러그인을 모아 둔 것으로 Babel 프리셋이라고 부른다.
```
# env preset 설치
$ npm install --save-dev @babel/preset-env
```

`package.json`
```json
{
  "name": "es6-project",
  "version": "1.0.0",
  "devDependencies": {
    "@babel/cli": "^7.2.3",
    "@babel/core": "^7.2.2",
    "@babel/preset-env": "^7.4.5"
  }
}
```

`.babelrc`
```json
{
  "presets": ["@babel/preset-env"]
}
```

#### 트랜스파일링
package.json 파일에 scripts를 추가한다. 완성된 package.json 파일은 아래와 같다.
```json
{
  "name": "es6-project",
  "version": "1.0.0",
  "scripts": {
    "build": "babel src/js -w -d dist/js"
  },
  "devDependencies": {
    "@babel/cli": "^7.2.3",
    "@babel/core": "^7.2.2",
    "@babel/preset-env": "^7.3.1"
  }
}
```
위 npm script는 src/js 폴더(타깃 폴더)에 있는 모든 ES6+ 파일들을 트랜스파일링한 후, 그 결과물을 dist/js 폴더에 저장한다. 사용한 옵션의 의미는 아래와 같다.
> -w : 타깃 폴더에 있는 모든 파일들의 변경을 감지하여 자동으로 트랜스파일한다. (--watch 옵션의 축약형)
> -d : 트랜스파일링된 결과물이 저장될 폴더를 지정한다. (--out-dir 옵션의 축약형)


<br/>

<br/>

## Reference
- [Babel과 Webpack을 이용한 ES6 환경 구축](https://poiemaweb.com/es6-babel-webpack-1)

<br/>

---

<br/>

## Homework 

### Challenge goals:

아래 주어진 4가지 목표를 모두 수행하여야 코딩챌린지를 통과할 수 있습니다.

- Make 4 routes: "/" , "/about-us" , "/contact" and "/protected"
- Each route should render a string with the name of the page, i.e: "/about-us" -> About Us.
- Make one middleware for all the routes, that middleware should console.log the message "I'm a middleware" on every request to any route.
- Make a middleware that won't allow me to go to "/protected", if I try to go to "/protected" I should be redirected back to "/"

This is the expected output:   
[![Video Label](http://img.youtube.com/vi/z-keQSxut7g/0.jpg)](https://youtu.be/z-keQSxut7g)

<br/>

### 조건:

- Use only ONE file: index.js
- There should be TWO middlewares. One is the "console" middleware and the other one is the "protected" middleware.
- There should be FOUR routes.

### 제출:
- CodeSandbox 템플릿 : [Day4 Boilerplate](https://codesandbox.io/s/express-blueprint-cedwx)
- 제출 : [Day4 Homework](https://codesandbox.io/s/express-blueprint-yh60q)
```js
import express from "express";

const app = express();

// Codesanbox does not need PORT :)

const handleHome = (req, res) => res.send("Home");

const handleAbout = (req, res) => res.send("About Us");

const handleContact = (req, res) => res.send("Contact");

const handleRedirect = (req, res) => res.redirect("/");

const middleware = (req, res, next) => {
  console.log("I'm a middleware");
  next();
};

app.use(middleware);

app.get("/", handleHome);

app.get("/about-us", handleAbout);

app.get("/contact", handleContact);

app.get("*", handleRedirect);

app.listen(() => console.log(`Listening!`));
```
- 정답 : [Day4 Answer](https://codesandbox.io/s/day-four-solution-5zdh2)
> Today's quiz is based on videos #2.0 to #2.2
  Don't worry, tomorrow we will start coding :) 


- 오늘의 강의: 유튜브 클론코딩 #2.0 to #2.2 
- 오늘의 과제: 위의 강의를 시청하신 후, 아래 퀴즈를 풀면 됩니다.  
- 제출기간: 익일 오전 6시까지

<br/>

[[노마드 코더] 유튜브 클론 코딩](https://academy.nomadcoders.co/courses/enrolled/435438)

`#2 ExpressJS`
- 2.0 What is a Server 
- 2.1 What is Express 
- 2.2 Installing Express with NPM 

<br/>
<!-- more -->

---

<br/>

## Lecture Summery

<br/>

### What is a Server 
서버란 어떤 특화된 임무를 수행하기 위해 설정된 컴퓨터이다. 지금 사용하고 있는 노트북이나 데스크탑도 서버라는 역할을 하면 서버 컴퓨터로 불린다. 

- 도메인 서버 : 도메인을 관리하는 서버
- 이메일 서버 : 이메일을 관리하는 서버
- 웹서버 : 웹사이트를 관리하는 서버, 호스팅 서버
- 멀티미디어 서버 : 동영상과 음악 파일을 관리하는 서버
- 이미지 서버 : 사진을 관리하는 서버
- 프린터 서버 : 프린터를 공유할 수 있도록 프린팅 작업을 관리하는 서버

<br/>

### What is Express
express는 서버를 만들 수 있는 매우 안정적인 Node.js 프레임워크

<br/>

### Node.js와 NPM 설치하기
Node.js 설치는 아래의 방법으로 할 수 있다. npm의 경우에는 Node.js를 설치시 함께 설치된다.

#### 공식사이트에서 패키지를 다운받아 설치하기
    [Node.js](https://nodejs.org/ko/)
    
<br/>
  
#### Homebrew로 설치하기 

- Homebrew 설치하기 : 아래의 명령어를 터미널에서 실행시켜준다. 
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

<br/>

- Homebrew 사용하기
```
# 버전확인
$ brew -v

# 명령어 확인
$brew help

# 패키지 설치
brew install <패키지이름> 
 
# 패키지 삭제
brew remove <패키지이름>
 
# 패키지 정보
brew info <패키지이름>
 
# 설치한 패키지의 최신버전을 설치
brew upgrade <패키지이름>
 
#설치한 패키지 목록
brew list 또는 brew ls
 
# Homebrew 업데이트
brew update
 
# 시스템 문제 확인
brew doctor
 
# 설치된 패키지의 최신 패키지 버전 확인
brew outdated
 
# 패키지 과거버전을 제거
brew cleanup
```

<br/>

- Node.js 설치하기
```
# 설치하기
brew install node

# Node 확인
node -v

# npm 확인
npm -v
```

    

<br/>

### npm
npm (노드 패키지 매니저/Node Package Manager)은 자바스크립트 프로그래밍 언어를 위한 패키지 관리자이다. 
자바스크립트 런타임 환경 Node.js의 기본 패키지 관리자이다.

- npm init : package.json 생성

    `package.json`
    > {   
          "name" : 해당 모듈의 이름을 정의한다.  (이름에 'node' 나 'js' 가 들어가면 안된다.)    
          "version" : 해당 모듈의 버전을 정의한다.   
          "description" : 해당 모듈의 추가적인 설명을 정의한다.   
          "main" : node에서 해당 package.json 을 탐색할 때 기준이 되는 파일 이름을 정한다.   
                      기본적으로 index 로 설정이 되며, 생략이 가능한 부분이지만 추후 프로젝트가 복잡해진다면 이 항목을 정의 할 필요가 있다.   
          "scripts" : package.json 이 있는 폴더에서 추가로 실행 할 스크립트 명령어를 정의한다. 노드 명령이나 쉘 스크립트를 적어주면 된다.  
                       start, test, build 등을 정의한다.   
          "author" : 해당 모듈의 제작자를 정의한다.   
          "liecnse" : 해당 모듈의 라이센스를 정의한다.   
          "dependencies" : 일반적으로 package.json 에 가장 많은 정보가 입력되는 곳 이며 여기서 모듈의 의존성을 정의 한다.   
                          해당 모듈이름과 버전을  키 : 값 의형식으로 정의 되어있다.   
          "devDependencies" : 해당 모듈의 실행에 필요한 또는 개발에 필요한 모듈의 의존성을 입력하는 곳 이다.    
      }
    
```
    {
      "name": "wetube",
      "version": "1.0.0",
      "description": "",
      "author": "alley",
      "license": "ISC",
      "dependencies": {
        "@babel/core": "^7.3.3",
        "@babel/node": "^7.2.2",
        "@babel/preset-env": "^7.3.1",
        "body-parser": "^1.18.3",
        "cookie-parser": "^1.4.4",
        "dotenv": "^7.0.0",
        "express": "^4.16.4",
        "helmet": "^3.15.1",
        "mongoose": "^5.4.19",
        "morgan": "^1.9.1",
        "pug": "^2.0.3"
      },
      "scripts": {
        "start": "nodemon --exec babel-node init.js --delay 2"
      },
      "devDependencies": {
        "nodemon": "^1.18.10"
      }
    }
```

<br/>

- 설치   
    package.json은 프로젝트에 대한 명세라고 할 수 있다. 해당 프로젝트의 이름, 버전, 사용되는 모듈 등의 스펙이 정해져 있으며, 이 package.json을 통해 모듈 의존성 모듈 관리도 진행할 수 있다. 만약 어떤 오픈 소스를 다운 받을 때 이 package.json만 있다면 해당 오픈 소스가 의존하고 있는 모듈이 어떤 것인지. 그리고 그 모듈들을 아래 명령어로 한 번에 설치할 수 있다.
```
npm install
```

<br/>

---

<br/>

## Homework 

### Quiz


1. A server is just a computer *   

    1) `True`  
    2) False   

<br/>

2. A server has to be online 24/7 *   

    1) `True`   
    2) False   

<br/>

3. A server can be on a private network *   

    1) `True`   
    2) False   

<br/>

4. A server is a computer without network access *   

    1) True   
    2) `False`   

<br/>

5. Any computer can be a server *     

    1) `True`   
    2) False   

<br/>

6. What is a framework *   

    1) `Lots of pre-made functions and utilities that somebody else wrote and that we can use`   
    2) Is a philosophy that we follow when we are programming   

<br/>

7. How does a framework help us *   

    1) It makes us better developers so we can make more money   
    2) `It helps us accomplish complex things in few lines of code`   

<br/>

8. What is the most popular NodeJS Framework *   

    1) KoaJS   
    2) SailsJS   
    3) `ExpressJS`   

<br/>

9. ExpressJS is not JS *   

    1) True   
    2) `False`   

<br/>

10. What does NPM stand for? *   

    1) Node Power Machine   
    2) Node Powder Manager   
    3) Node Package Mama   
    4) `Node Package Manager`   

<br/>

11. What is NPM *   

    1) It's a tool that makes my NodeJS code run faster   
    2) `Is a tool to download and share NodeJS packages`   

<br/>

12. ExpressJS is published as an NPM Pacakge *   

    1) `True`   
    2) False   

<br/>

13. How can I create a NodeJS project *   

    1) `Create a package.json`   
    2) Run 'node init'   

<br/>

14. What is "package.json" *   

    1) Is a file where I write the code for my server   
    2) `Is a file where I save information about my project and the packages it needs to run`   
    3) Is a file to save the user's data   

<br/>

15. How can I install Express *   

    1) node install express   
    2) npm add express   
    3) `npm install express`   

<br/>

16. What is the node_modules folder *   

    1) `Is where all the installed packages go`   
    2) Is where I put the code I want to publish   
    3) Is where I put the code I don't need anymore   

<br/>

17. Why I should never share / upload my "node_modules" *   

    1) Because the code there is private   
    2) `Because I can just share the package.json`   
    3) Because I don't have the upload license   

<br/>

18. If I delete "node_modules" how can I reinstall my dependencies from my package.json *   

    1) Running: "npm install dependencies"   
    2) `Running: "npm install"`   
    3) Running: "npm reinstall"   