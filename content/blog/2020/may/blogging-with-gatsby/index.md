---
title: Blogging with Gatsby (Gatsby로 블로그쓰기)
date: "2020-05-08T22:40:32.169Z"
description: How to write blog posts with Gatsby, using markdown. 마크다운으로 블로그 쓰는법, 개츠비로 블로그 커스터마이징 하는 법 정리.
---

Gatsby에서 블로그 포스트는 Markdown 문법으로 쉽게 쓸 수 있다. The gatsby-source-filesystem plugin reads files from your computer. The gatsby-transformer-remark plugin makes the contents of your Markdown files available to GraphQL [(taken from Gatsby)](https://www.gatsbyjs.org/docs/glossary/markdown). GraphQL is a query language invented at Facebook to pull needed data into React components [(read more from here)](https://www.gatsbyjs.org/docs/graphql-concepts/). Gatsby starter를 통해 플러그인 설치 설정은 자동으로 끝났으니 I'll just jump right into creating a markdown post.

### Frontmatter

**1. 파일 만들기**<br>
내가 설치해준 gatsby-starter-blog 에서는 content/blog 디렉토리 안에 각 포스트 폴더를 생성해 준 후 그 폴더안에 index.md 파일을 만들어준다. 이 블로그 포스트는 content/blog/blogging-with-gatsby/index.md 에 쓰고있다.

**2. Frontmatter 써주기**<br>
index.md 파일 맨 위에에는 Frontmatter 이라고 불리는 파일 정보를 적어준다. 이 정보를 작성 해 주어야 GraphQL이 파일 정보를 처리할 수 있게 된다. Frontmatter 안에는 여러 정보가 들어갈 수 있는데 나는 우선 세가지 꼭 필요한 정보만 적어주었다
``` md
---
title: "My first blog post"
date: "2020-05-09T22:40:32.169Z"
description: "blog post description goes here"
---
```
- title: 해당 블로그 포스트의 타이틀이다
- date: 블로그가 작성된 날짜와 시간. 이 날짜에 따라 홈페이지에 블로그 포스트 나열 순서가 달라진다. "2020-05-09" 같은 좀더 간단한 포맷을 쓸수도 있지만 같은날 다른 블로그 포스트를 몇개 쓸수도 있어서 시간도 포함해주기로 했다.
  - ISO 8601 이라는 포맷, YYYY-MM-DD HH:MM:SS +/-TTTT
  - [자바스크립트를 통해 현재 시간을 ISO 8601 포맷으로 받는 코드를 짜보았다.](../js-date-time)
- description: 블로그의 간단한 설명. 블로그 홈페이지에서 타이틀 밑에 이 내용이 들어간다.
- 나중에는 slug, category, tags 등의 정보도 추가할 예정이다.

### Markdown
Markdown 문법은 이곳 참고하기
- [Gatsby Markdown Syntax](https://www.gatsbyjs.org/docs/mdx/markdown-syntax/)
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)