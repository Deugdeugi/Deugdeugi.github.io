---
title: npm install 옵션 종류
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

npm install 명령어의 옵션에 대해 정리해 보았다

<!-- more -->

<h2 id="h1">1. 패키지 설치</h2>
<span class='thirdheading'>
1) 패키지명을 명시해 특정 패키지를 설치함
</span>
```
$ npm install <package>
```

<br>
<span class='thirdheading'>
2) 패키지명을 명시하지 않고 package.json 파일의 의존성을 설치함
</span>
```
$ npm install
```


<br>
<h2 id="h2">2. 지역 설치와 전역 설치</h2>
<span class='thirdheading'>
1) 지역(local) 설치 (default)
</span>

- 프로젝트 루트 디렉토리에 node_modules 디렉토리가 자동 생성되고 그 안에 패키지가 설치된다.
- 지역으로 설치된 패키지는 해당 프로젝트 내에서만 사용할 수 있다.

```
$ npm install <package>
```

<br>
<span class='thirdheading'>
2) 전역(global) 설치
</span>
- 전역으로 설치된 패키지는 전역에서 참조할 수 있다.
- 모든 프로젝트가 공통으로 사용하는 패키지는 전역에 설치한다.
- 전역에 설치된 패키지는 OS에 따라 설치 장소가 다르다.
    - macOS  /usr/local/lib/node_modules
    - window  c:\Users\%USERNAME%\AppData\Roaming\npm\node_modules

```
$ npm install -g <package>
```

<br>
<h2 id="h3">3) npm install 명령어 옵션</h2>

--save 옵션은 package.json의 dependency 항목에 모듈을 추가한다는 의미로, npm@5 부터 --save 옵션을 기본 옵션으로 저장한다.

1) -P (--save-prod) : dependencies에 패키지를 등록. 프로젝트가 배포 시 사용될 의존성 모듈을 정의하고 설치한다. (defalut)

2) -D (--save-dev) : devDependencies에 패키지를 등록. 개발 단계에서만 사용하는 의존성 모듈을 정의하고 설치한다.

3) -O (--save-optional) : optionalDependencies에 패키지를 등록. 선택적 의존성 모듈읠 정의하고 설치한다.

4) --no-save : dependencies에 패키지를 등록하지 않는다.

5) -E (--save-exact) : dependencies에 패키지를 등록.npm의 기본 SemVer 연산자를 사용하는 대신 정확한 버전으로 설치한다.

6) -B (--save-bundle) :  bundleDependencies에 패키지를 등록. 번들로 묶을 패키지 의존성 모듈을 정의하고 설치한다.

<br>
<h2 id="h4">4) 유의적 버전(Semantic versioning)</h2>

버전 정보가 2.3.1이라고 하면,<br>
2 : major version<br>
3 : minor version<br>
1 : patch version 이다.

<br>
버전 정보 표기 방법은 아래 표와 같다.

|표기법|설명|
|---|---|
|version|명시된 version과 일치|
|>version|명시된 version보다 높은 버전|
|>=version|명시된 version과 같거나 높은 버전|
|<version|명시된 version보다 낮은 버전|
|<=version|명시된 version과 같거나 낮은 버전|
|~version|명시된 version과 근사한 버전|
|^version|명시된 version과 호횐되는 버전|

<br>
<span class='thirdheading'>
※ ~(틸트)와 ^(캐럿)의 차이?
</span>

1) ~(틸트) : 틸트는 패치 버전 범위 내에서 업데이트 한다.

```
ex)
~0.0.1 : 0.0.1 <= version < 0.1.0
~0.1.1 : 0.1.1 <= version < 0.2.0
```

<br>
2) ^(캐럿) : 캐럿은 마이너 버전 범위 내에서 업데이트 한다.
```
ex)
^1.0.2 : 1.0.2 <= version < 2.0
```

<br>
<h2 id="h4">출처</h2>
[https://ahnsisters.tistory.com/16](https://ahnsisters.tistory.com/16)