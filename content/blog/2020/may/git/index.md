---
title: Git Review
date: "2020-05-28T12:40:32.169Z"
description: Git for team collaboration
---

# git

```jsx
내 브랜치에서
git add .
git commit -m ""
//commit 하고나서 master 로 갈 수 있다.
git checkout master
git pull origin master //내파일과 master 로 비교한다 동일하면
git checkout feature/jl
git branch //확인해보기
git push origin feature/jl
// 주소가 뜨면 cmd 링크
```

git flow

Local: 내컴퓨터

Remote: github

github 을 로컬에 클론하면 Master Branch 가 생성이된다.

No conflict flow

```
- Master branch 에서 시작
git branch feature/branch
git checktout feature/login
- 브랜치에서 작업
git add .
git commit
git push origin feature/login
//origin 에 내가 만든 feature/login 을 push 하겠다
//remote 에 feature/login 이 생성이 된다
- pull request (master 에게 pull 요청 merge 시켜달라 요청)
- merge 가 되면 master 가 업데이트
//이제 local 에 있는 master 를 update 해줘야한다
git checkout master //master 로 이동한 후
git pull origin master //merge 된 master branch 를 가져온다
```

다른 사람의 업데이트를 pull해서 받아오면

git checkout feature/login

git merge //내 브랜치와 merge

이때 conflict 가 일어나면 conflict 해결

git add

git commit

git push

git status 로 항상 상태 확인해주기

git checktout feature

git add .

git commit

git checkout master

git pull origin master

git checkout feature

git merge master

// 이럴경우 conflict 가 일어나기도 한다.

pr 성공후

git branch feature/newbranch

git checkout feature/newbranch
