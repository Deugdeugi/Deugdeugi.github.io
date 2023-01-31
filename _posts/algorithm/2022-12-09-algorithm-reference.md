---
title: 알고리즘에 많이 쓰이는 함수 & 라이브러리
tags: Algorithm_Basic
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

알고리즘 풀이에 많이 쓰이는 함수 & 라이브러리를 모아두었다

<!-- more -->
<h2 id="h1">C언어</h2>

<h2 id="h2">C++</h2>

<h2 id="h3">파이썬</h2>
#### 1) 파이썬에서 재귀를 사용하여 문제를 해결할 때는 다음 코드를 사용한다.
=> 파이썬의 기본 재귀 깊이 제한은 1000으로 매우 얕은 편이기 때문에, 재귀로 알고리즘 문제를 풀 경우 자주 이 제한에 걸리게 된다.
```python
import sys
sys.setrecursionlimit(10 ** 6)
```