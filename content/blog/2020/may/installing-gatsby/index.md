---
title: Installing Gatsby (Gatsby로 블로그하기)
date: "2020-05-07T22:40:32.169Z"
description: This post is about my frustrating but fulfilling experience about installing Gatsby blog. 진입장벽이 정말 높았던 개츠비 블로그 설치과정을 공유하려고 한다.
---

내가 블로그를 시작하기전 꼭 원했던 조건은 커스터마이징이 가능할 것, github 에 호스팅 할 것 이었다. 먼저 Jekyll로 블로그를 시작했다가 Gatsby 가 리액트 기반이라는 것을 알았을 때 Gatsby 로 갈아타기로 결심했다. 부트캠프 세션을 통해 설치를 해보았는데 혼자 다시 해봐야겠다는 오기가 생겨 새로 설치를 시도했다가 에러란 에러는 다 만났다. 구글링을 통해 해결해보겠다고 별의별 command 를 다 써보다가 결국은 OS 를 다시 설치해야 하는 상황까지 갔다 (lesson learned: terminal command 함부로 만지지 말기 ㅠㅠ). 다음은 clean 한 macOS Catalina 에서 Gatsby 블로그 설치 과정을 정리한 것이다. 

### Initial Requirements

**1. Xcode 설치하기**<br>
App store 나 Terminal 을 이용해 Xcode 를 설치해 준다.

**2. Git 설치 확인하기**<br>
macOS에는 git이 설치되어 있다. git -- v 명령어로 버젼을 확인한다.

**3. Homebrew 설치하기**<br>
Terminal 을 이용해 [Homebrew](https://brew.sh/) 를 설치해 준다.
``` console
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

**4. Node 설치하기**<br>
``` console
brew install node
```
- node 는 npm 과 함께 설치된다. node -v, npm -v 명령어을 통해 잘 설치되었는지 확인한다.

### Gatsby 설치하기

**1. Gatsby CLI 설치하기**<br>
Gatsby CLI 는 개츠비 블로그를 만들 수 있도록 해주는 npm 패키지 이다. Terminal 에서 npm 명령어로 설치해준다.
``` console
npm install -g gatsby-cli
```
- sudo 명령어를 쓰지 않고도 잘 설치될 수 있어야 한다.
- gatsby -v 로 잘 설치 되었는지 확인해보기

**2. Gatsby 블로그 만들기**<br>
지금까지는 블로그를 설치할 수 있는 환경을 만들어 주었다면 이제는 진짜 블로그 파일을 설치해 줄 시간이다. Gatsby starter를 이용해 블로그 만들기. starter는 theme과 같은 개념이다. [Starter Library](https://www.gatsbyjs.org/starters)에서 고를 수 있다. 난 커스터마이징을 원하므로 기본적인 gatsby-starter-blog 를 설치하기로 했다. Terminal 에서 원하는 directory 로 간 후 starter 를 설치해준다. 난 documnets/codes 폴더에 설치했다.
``` console
cd documents
cd codes
gatsby new blog https://github.com/gatsbyjs/gatsby-starter-blog
```

**3. 잘 설치되었는지 확인하기**<br>
documents/codes 안 blog 폴더안에 블로그가 설치 되었다. Terminal 에서 blog 폴더로 들어간 다음 로컬서버에서 블로그를 띄어준다.
``` console
cd blog
gatsby develop
```
- 브라우저 주소창에서 localhost:8000으로 접속해서 블로그가 나타나면 설치 성공이다.

### Gatsby 블로그 쓰기
이부분은 다른 포스트에 따로 정리할 예정

### Github 에 블로그 호스트하기

**1. gh-pages 패키지 설치하기**<br>
Github pages 에 publish 하기 위해서는 gh-pages 브랜치에 push 를 해주어야한다. gh-pages 패키지를 설치하면 gh-pages 브랜치를 만들어주고 push 할 수 있도록 해준다.
``` console
npm install gh-pages --save-dev
```

**2. Github에서 Repository 만들기**<br>
난 blog 라는 path 안에 블로그를 호스트 하고 싶었다. 그래서 blog 라는 repo 를 만들었다. 내 블로그 주소는 [brandnewjinah.github.io/blog](https://brandnewjinah.github.io/blog)가 되었다.

**3. Repo 에 연동하기**<br>
repo 를 처음 만들면 나오는 화면에서 내 git 주소를 복사해온 후 다음 명령어를 써준다.
``` console
git init
git remote add origin https://github.com/brandnewjinah/blog.git
```
- blog repo 를 만들다 지웠다 다시 만들으니 fatal: remote origin already exists 라는 에러메시지가 나왔다.
- git remote <mark>set-url</mark> origin https://github.com/brandnewjinah/blog.git 명령어로 해결.

**4. gatsby-config.js 에 내 블로그 주소 설정해주기**<br>
처음 설치한 gatsby-starter-blog 의 config 파일에는 dummy 주소가 적혀있다. 들어가서 내 블로그 주소로 바꿔 주어야 한다.
``` javascript
module.exports = {
  siteMetadata: {
    title: `블로그 타이틀`,
    author: {
      name: `내이름`,
      summary: `내설명`,
    },
    description: `짧은 블로그 설명`,
    siteUrl: `https://brandnewjinah.github.io/`,
  },
  pathPrefix: `/blog`,
```
난 blog 라는 path 안에 블로그를 호스팅 하고 싶기 때문에 pathPrefix: `/blog` 를 넣어주는것이 매우 중요하다. 이걸 넣어주어야 내 블로그 포스트나 페이지가 brandnewjinah.github.io/blog/... 로 지정이 된다.

**5. package.json 에 deploy 더해주기**<br>

package.json 파일에 들어가서 scripts 안에 deploy를 더해준다. 이 명령어가 있어야 git 에 블로그를 push 해줄 수 있다.
``` javascript
{
  "scripts": {
    "deploy": "gatsby build --prefix-paths && gh-pages -d public"
  }
}
```

### Github 에 deploy 하기

**1. 처음 push 하기**<br>
Terminal 에서 다음 명령어를 써준다.
``` console
git add .
git commit -m "first commit"
git push origin master
```

**2. deploy 하기**<br>
``` console
npm run deploy
```
- 이때 package.json deploy 에러가 났다. package.json 파일에는 아무 문제가 없었는데 에러가 나서 아마 문제는 npm 자체에 문제가 아닐까 해서 gatsby 패키지를 지우고 다시 install 하니까 문제가 해결됬다.
- ``` console
npm uninstall -g gatsby-cli
npm install -g gatsby-cli
```
- 이제 brandnewjinah.github.io/blog 에 가서 잘 설치 되었는지 확인할 수 있다.

**3. develop 브랜치 만들어주기**<br>
부트캠프 멘토님께서 develop 브랜치 생성의 필요성을 설명해 주셨는데 아직 확실히 이해가 안된다. 우선은 생성해주었고 develop 브랜치에서 push, deploy 하도록 했다. 이해가 되면 이곳에 정리하기.

``` console
git branch develop
git checkout develop
git add .
git commit -m “posting”
git push -u origin develop
npm run deploy
```

야호 이젠 나도 gatsby 블로그가 있다!!