---
title: Promise / async / await
tags: Javascript
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

맨날 알다가도 모르겠는 Promise / async / await 에 대해 정리해 보았다

<!-- more -->

## 1. 콜백
- 아래 코드와 같이 callback 함수를 받아 함수 동작이 끝난 후 실행할 수 있다.
- 하지만... 비동기 동작이 하나씩 추가될 때마다 중첩 호출이 만들어내는 '피라미드’는 오른쪽으로 점점 커진다. 이를 ‘콜백 지옥(callback hell)’ 혹은 '멸망의 피라미드(pyramid of doom)' 라고 한다.
- 각 비동기 동작을 함수로 각각 만들어서 해결할 수는 있지만... 그렇게 하면 함수의 재사용이 불가능해진다.

```javascript
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;

  script.onload = () => callback(script);

  document.head.append(script);
}
```

## 2. Promise / async / await
- 아래 사이트에 자세히 설명되어 있다. <br>
[https://ko.javascript.info/async](https://ko.javascript.info/async)

- 만약 따로 기록할 내용이 있으면 추가할 예정이다.

## 출처
- [https://ko.javascript.info/async](https://ko.javascript.info/async)