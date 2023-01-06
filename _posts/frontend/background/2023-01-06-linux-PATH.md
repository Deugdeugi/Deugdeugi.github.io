---
title: 리눅스 환경변수(PATH)에 대하여 정리해보자
tags: Frontend FrontendBack
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

node/npm 설치 과정에서 환경변수 때문에 동작이 좀 꼬여서... 이 기회에 환경변수에 대해 정리해 보았다

<!-- more -->

<h2 id="h1">1. PATH 환경변수란?</h2>
- 터미널에서 명령어를 입력하면, 그 실행 파일을 OS가 찾는다. 이 실행 파일의 위치를 PATH 환경변수에서 찾는다.
- PATH에 설정된 명령어는 명령어만 쳐도 실행이 된다.
- PATH에 설정되지 않은 명령어는 명령어의 절대경로를 모두 입력해야 한다.
- PATH 안의 경로들은 /usr/bin:/etc:/usr/local/bin과 같이 콜론(:)으로 구분되어 있다.

<h2 id="h2">2. 명령어 찾는 순서</h2>
1) /etc/profile

2) /etc/bashrc

3) /etc/inputrc

4) $HOME/.bash_profile

5) $HOME/.bashrc

6) $HOME/.inputrc

<br>

<h2 id="h3">3. 환경변수 추가/확인/제거하는 방법</h2>
1) 리눅스 환경변수 일시 적용 => 시스템 재부팅 또는 로그아웃을 하면 환경 변수 값이 사라지게 된다.
```
$ export PATH = <추가할 경로>:$PATH
```

<br>

2) 리눅스 환경변수 영구 적용 => 사용자 세션이 열릴 때마다 export 명령어를 수행하면 된다.
- /etc/bash.bashrc 파일을 열어서 맨 마지막 줄에 적용하고자 하는 환경변수를 export 명령어로 설정한다.
- 특정 사용자에게만 환경 변수를 영구적으로 적용하고 싶은 경우 ~/.bashrc 파일을 같은 방법으로 수정하면 된다.
```
(ex) export JAVA_HOME=/usr/java/jdk1.6.0_45
```

<br>

3) 환경변수 확인
```
1) 전체 확인
$ env

2) 특정 환경 변수 확인
$ env | grep 환경변수명
```

<br>

4) 환경변수 해제
```
$ unseet 환경변수명
```

<br>

<h2 id="h4">출처</h2>
[https://tigercoin.tistory.com/39](https://tigercoin.tistory.com/39) <br>
[https://devpouch.tistory.com/125](https://devpouch.tistory.com/125)