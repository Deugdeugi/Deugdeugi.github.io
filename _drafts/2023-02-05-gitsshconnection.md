---
title: Github ssh 접속 원리 정리
tags: Tool Git
aside:
  toc: true
sidebar:
  nav: docs-en
# cover: /assets/images/cover1.jpg
# article_header:
#   type: cover
#   image:
#     src: /assets/images/cover2.jpg
---

회사에서 업무를 하다 보니 git push를 할 때 github에 ssh로 자동 로그인되는 아이디가 있어서 이 아이디로 왜 접속되는지 궁금했다...

<!-- more -->
<br>
<h2 id="h1">commit을 하고 push를 하려던 어느 날...</h2>
회사에서 프로젝트를 하던 도중, commit을 하고 push를 하려고 하니 오류가 발생했다.
해당 오류는 아래의 오류였다.
```
Permission to (repositoryName) denied to (userName)
```
보시다시피, 내용 그대로 이 레포지토리에 대한 해당 유저의 권한이 없다는 오류이다.
이전에는 Github 레포지토리에 유저를 Collaborator로 등록하는 방식으로 해결했었다. 그런데 생각해보니, 나한테는 github 아이디가 두 개 있었는데 한 아이디로만 접속되는 것이었다.
왜 push를 하려고 하면 특정 github 아이디로만 접속이 되는지 궁금해졌다.

☀︎ github ssh 접속 과정은 다음 명령어로 확인할 수 있다.
옵션에 v를 넣으면 더욱 자세하게 접속 과정을 확인할 수 있으며, 3개까지 추가할 수 있는 것 같다.
```
(ex) ssh -vT git@github.com
```

<br>
<h2 id="h2">답을 찾는 과정 1 : .ssh/config 파일</h2>
검색을 하다 보니, ssh keygen으로 key를 만든 후 ~/.ssh/config 파일에 지정을 해서 특정 유저로 로그인하도록 할 수 있었다.
[https://jintaewoo.tistory.com/44](https://jintaewoo.tistory.com/44)
<br> [https://www.lesstif.com/gitbook/git-push-error-repository-not-found-129008566.html](https://www.lesstif.com/gitbook/git-push-error-repository-not-found-129008566.html)

... 하지만 요거로는 아직 수수께끼가 다 풀리지 않았다ㅠㅠ
아까 로그인되던 특정 아이디는 굳이 ~/.ssh/config 파일에 등록이 되어 있지 않아도 로그인이 됐었다. 거기다 더 골때리는 건, .ssh 폴더 자체가 없어도 해당 아이디로 github ssh 로그인은 잘 되고 있었다는 거다...

<br>
<h2 id="h3">답을 찾는 과정 2 : ssh 접속 과정 자체를 보자.</h2>

... 쓰면서 맥이랑 윈도우로 다시 시도해 보니 요것들은 잘 되는데...? 우분투만 뭔가 이상한 것 같다.
다음 항목에 따라 테스트를 해보려고 한다.



접속 명령어는 ssh -vT git@github.com 이다.
1. 기본 id_rsa 접속 확인
2. ssh config로 지정한 후 접속 확인
3. .ssh 폴더나 id_rsa를 숨기고 접속 확인

SSH 키 이용 시 bad permissions: ignore key: 에러가 발생할 경우 : https://www.deok.me/entry/SSH-%ED%82%A4-%EC%9D%B4%EC%9A%A9-%EC%8B%9C-bad-permissions-ignore-key-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EA%B2%BD%EC%9A%B0
SSH 키 생성 후 오류 : https://m.blog.naver.com/PostView.nhn?isHttpsRedirect=true&blogId=zilly1&logNo=220923646151
Github 다수 계정을 위한 SSH key 설정 :: 마이구미 : https://mygumi.tistory.com/96