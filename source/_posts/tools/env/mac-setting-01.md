---
title: macOS 개발환경 기본설정
toc: true
thumbnail: images/gallery/thumbnails/macbook.jpg
categories:
  - tools
  - env
tags:
  - mac
  - 개발환경
  - 기본설정
date: 2019-11-10 12:20:22
---

## Overview
MacOS 기본 환경 설정을 위한 가이드입니다.
저를 포함해 많은 분들에게 도움이 될 수 있었으면 좋겠습니다.

<br/>

<br/>

<!-- more -->

## 기본 설정

### Finder 숨김 폴더 및 파일 노출 설정
- Finder 에서 숨겨진 폴더 또는 파일을 보여주거나 숨기고 싶을 때 아래와 같은 단축키로 제어할 수 있습니다.
- `command` + `shift` + `.`

<br/>

<br/>

### Finder 기본 폴더 설정
- Finder 실행 시 기본 폴더를 Home 폴더로 설정합니다.
- General > New Finder windows show: (home folder)

<br/>

<br/>

### 파일 확장자 보여주기
- 모든 파일의 확장자를 보여주는 설정은 아래와 같습니다.
- `Advanced` > `Show all filename extensions`: 체크하세요.

<br/>

<br/>

### 모든 텍스트 자동 변경 옵션 끄기
- `Keyboard` > `Text`: 모든 자동 변경 옵션 끄기
- 입력한 단어를 컴퓨터 마음대로 바꾸는 걸 방지
- 특히 Use smart quotes and dashes는 코드 복사하다가 따옴표가 바뀌면서 고생이 시작됨

<br/>

<br/>

<br/>

<br/>

## 필수 프로그램

### Xcode
macOS에서 `gcc`, `make` 같은 컴파일 도구를 사용하려면 기본적으로 Homebrew 또는 명령어 라인 도구(Command Line Tools)을 먼저 설치해야 합니다.

Command Line Tools는 Xcode를 설치하면 자동으로 같이 설치됩니다.

하지만, Xcode 용량이 크고 모든 사람이 IDE가 필요한 게 아니므로 명령어 도구만 따로 설치하겠습니다.

{% gdemo_terminal 'xcode-select --install' '70px' 'zsh' '500' '$' 'demo-teriminal1' %}
{% endgdemo_terminal %}

<br/>

<br/>

### Homebrew
> Homebrew는 macOS 용 패키지 관리자로, 필요한 프로그램을 설치하는 데 용이합니다.

{% gdemo_terminal '/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"' '70px' 'zsh' '500' '$' 'demo-teriminal2' %}
{% endgdemo_terminal %}

- [Homebrew 홈페이지](https://brew.sh/)
- [brew 명령어](https://docs.brew.sh/Manpage.html)
- [brew 패키지 검색](https://formulae.brew.sh/)

<br/>

<br/>

### git
Version 관리 도구로 macOS에 기본으로 설치되어 있지만 최신 버전이 아니므로 brew를 이용하여 업데이트 합니다.

아래 순서대로 우선 시 됩니다.

1. `.git/config` : 이 파일은 Git 디렉토리에 있고 특정 저장소(혹은 현재 작업 중인 프로젝트)에만 적용됩니다.
2. `~/.gitconfig` : 특정 사용자에게만 적용되는 설정이다. git config –global 옵션으로 이 파일을 읽고 쓸 수 있습니다.
3. `/etc/gitconfig` : 시스템의 모든 사용자와 모든 저장소에 적용되는 설정이다. git config –system 옵션으로 이 파일을 읽고 쓸 수 있습니다.

{% gdemo_terminal 'brew install git' '70px' 'zsh' '500' '$' 'demo-teriminal7' %}
{% endgdemo_terminal %}

```
git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"
git config --global core.precomposeunicode true
git config --global core.quotepath false
```

- [git](https://git-scm.com/)

<br/>

<br/>

<br/>

<br/>

## 터미널 설정

### iTerm2
macOS에 기본으로 설치되어 있는 Terminal 앱 대신 iTerm2를 터미널 앱으로 사용합니다.  
iTerm2는 기본 앱에 없는 다양한 기능이 있고 손쉽게 테마를 설정할 수 있습니다.

#### 설치

{% gdemo_terminal 'brew cask install iterm2' '70px' 'zsh' '500' '$' 'demo-teriminal8' %}
{% endgdemo_terminal %}

<br/>

<br/>

#### 테마선택
[여러개의 테마](https://iterm2colorschemes.com/) 중 마음에 드는 것을 골라 다운로드 한 뒤, 파일을 더블클릭 하면 자동으로 `iTerm color Preset`에 추가됩니다.

<br/>

<br/>

#### 테마적용
iTerm을 실행하고 설정(`⌘` + `,`)창에서 Profiles 항목을 선택하고 Colors탭을 선택합니다.
테마 및 컬러설정, 타이틀바, 스크롤바 등의 수정을 할 수 있습니다.

<br/>

<br/>

<br/>

### zsh 
macOS 의 기본 shell은 bash 를 대체할 zsh를 설치합니다.

- 컨텍스트 기반 자동완성 기능(tab)
- 다양하고 예쁜 테마와 플러그인
- 스펠링 체크
- history 기능

{% gdemo_terminal 'brew install zsh;chsh -s $(which zsh)' '70px' 'zsh' '500' '$' 'demo-teriminal3' %}
{% endgdemo_terminal %}

<br/>

<br/>

### oh-my-zsh
zsh과 oh-my-zsh의 조합으로 강력한 쉘을 사용할 수 있게 되었습니다. 여기서 모든 기능을 설명할 순 없지만 자주 사용하는 몇 가지 팁을 소개합니다.

- 명령어가 기억나지 않으면 tab을 누르세요
- cd ../.. 대신 ..., ...., ....., …
- 단축명령어 - git status => gst, git pull => gl 등등 다양한 [단축명령어](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/git/)

{% gdemo_terminal 'sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"' '70px' 'zsh' '500' '$' 'demo-teriminal4' %}
{% endgdemo_terminal %}

<br/>

<br/>

#### oh-my-zsh 테마변경
oh-my-zsh에서 제공하는 [Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/themes) 를 확인하고 `~/.zshrc`를 열고 테마명을 지정해주면 테마를 설정 할 수 있습니다.

<br/>

<br/>

<br/>

<br/>


## 개발환경 설정

### NVM 설치 및 설정

개발 환경이나 필요에 따라 다양한 node.js의 버전을 사용해야 하는 경우가 있습니다.

NVM은 `Node Version Manager`로, 다양한 버전 node.js를 설치할 수 있으며 설치 한 Node version을 간단한 명령어로 전환 할 수 있습니다.

brew를 통한 아래 명령어로 쉽게 설치 하세요.

{% gdemo_terminal 'brew install nvm' '70px' 'zsh' '500' '$' 'demo-teriminal9' %}
{% endgdemo_terminal %}

<br/>

<br/>

#### Node 버전 및 설치 유무 확인

{% gdemo_terminal 'node —version' '70px' 'zsh' '500' '$' 'demo-teriminal10' %}
{% endgdemo_terminal %}

<br/>

- 이미 설치되어 있다면 아래와 같이 삭제합니다.

{% gdemo_terminal 'brew uninstall --force node' '70px' 'zsh' '500' '$' 'demo-teriminal10-1' %}
{% endgdemo_terminal %}

<br/>

<br/>

#### NVM 환경변수 및 설정 내용 추가

- `.zshrc` 파일을 열어 하단에 아래 내용을 추가 한 후 저장합니다.

{% codeblock .zshrc %}

# NVM

export NVM_DIR="$HOME/.nvm"
. "$(brew --prefix nvm)/nvm.sh"
{% endcodeblock %}

<br/>

<br/>

- `.zshrc` 파일을 읽어 파일 내 내용을 실행시켜 적용합니다.

{% gdemo_terminal 'source .zshrc' '70px' 'zsh' '500' '$' 'demo-teriminal10-2' %}
{% endgdemo_terminal %}

<br/>

<br/>

#### NVM을 통한 Node 설치 및 버전 전환

{% gdemo_terminal 'nvm install 10.15.3;nvm use 10.15.3' '70px' 'zsh' '500' '$' 'demo-teriminal10-3' %}
{% endgdemo_terminal %}

<br/>

<br/>

### Yarn 설치

수많은 개발자들은 코드의 패키지를 공유하고 이 것을 조립하여 프로젝트를 빌드하는 도구로 Package Manager를 사용합니다.

그리고 전 세계적으로 가장 인기있고 많이 쓰이는 JavaScript Package Manager는 `NPM` 입니다.

NPM은 배포가 쉽고 종속성을 쉽게 해결할 수 있다는 장점이 있지만 패키지가 중복으로 설치될 수 있다는 단점이 있습니다.

이러한 이슈를 해결하기 위한 새로운 자바스크립트 패키지 매니저가 `Yarn`입니다.

1. NPM3보다 패키지 설치 속도가 빠릅니다.

2. JSON 포맷을 사용하지 않습니다.

3. 오프라인 모드가 가능합니다.

<br/>

<br/>

{% gdemo_terminal 'brew install yarn' '70px' 'zsh' '500' '$' 'demo-teriminal11' %}
{% endgdemo_terminal %}

<br/>

<br/>

### SSH Key 설정

`새로운 SSH key 생성하기`

1. Termial을 열어 Github 이메일 주소와 함께 아래와 같이 붙여넣습니다.

{% gdemo_terminal 'ssh-keygen -t rsa -b 4096 -C "<your_email@example.com>"' '70px' 'zsh' '500' '$' 'demo-teriminal13-1' %}
{% endgdemo_terminal %}

<br/>

2. 새로운 ssh key가 생성되고, "Enter a file in which to save the key,"라는 문구가 뜬다면, `Enter` 키를 눌러주세요.

3. 아래와 같은 내용이 뜬다면, `Enter` 키를 눌러주세요.

```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

4. 생성된 ssh key 내용을 복사합니다.

{% gdemo_terminal 'pbcopy < ~/.ssh/id_rsa.pub' '70px' 'zsh' '500' '$' 'demo-teriminal13-2' %}
{% endgdemo_terminal %}

<br/>

5. [Add New SSH keys on Github](https://github.com/settings/ssh/new) 에 접속하여 `Title`에는 userName을, `Key`에는 복사한 내용을 붙여넣고 추가합니다.


<br/>

<br/>

<br/>

<br/>

## 필요한 어플리케이션 설치

### chrome 설치

{% gdemo_terminal 'brew cask install google-chrome' '70px' 'zsh' '500' '$' 'demo-teriminal12' %}
{% endgdemo_terminal %}


<br/>

<br/>

### alfred
alfred는 독특한 단축키와 키스트로크 시스템을 통해 생산성을 높여줍니다.

- 앱을 실행하고 파일을 찾고 계산하는 것은 물론 빠르고 정확하게 맥을 제어할 수 있습니다.
- 사용자 설정 기능도 강력합니다.
- MacOS의 단점인 스폿라이트(spotlight)를 훌륭하게 보완한 앱입니다.

{% gdemo_terminal 'brew cask install alfred' '70px' 'zsh' '500' '$' 'demo-teriminal5' %}
{% endgdemo_terminal %}

<br/>

<br/>

### divvy
divvy는 사용자가 화면 창의 크기와 위치를 마음대로 조절 할 수 있습니다.

- free trial version 을 사용합니다.
- `시스템설정` > `사용자그룹` > `로그인 항목`
- `설정` > `보안 및 개인정보보호` > `손쉬운 사용` 내 하단의 자물쇠 버튼을 클릭하여 `Divvy.app` 체크박스 활성화

{% gdemo_terminal 'brew cask install divvy' '70px' 'zsh' '500' '$' 'demo-teriminal6' %}
{% endgdemo_terminal %}


---

## Reference
- [본격 macOS에 개발 환경 구축하기](https://subicura.com/2017/11/22/mac-os-development-environment-setup.html)
- [Mac OS 개발 환경 설정 Guide](https://lunarscents.github.io/2019/08/17/developmentEnvironmentInMac/#more)


