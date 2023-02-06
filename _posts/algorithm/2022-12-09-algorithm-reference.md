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

<br>
#### 2) 파이썬에서 리스트를 만들 때는 리스트 컴프리헨션(list comprehension)을 자주 쓰게 된다.
```python
# 0~9 숫자 중 2의 배수인 숫자(짝수)로 리스트 생성
>>> a = [i for i in range(10) if i % 2 == 0] 
>>> a
[0, 2, 4, 6, 8]
```

![Image](/assets/postimage/listcomprehension_1.png){:.border}

<br><br>
```python
# 2단부터 9단까지 구구단을 리스트 생성
>>> a = [i * j for j in range(2, 10) for i in range(1, 10)]
>>> a
[2, 4, 6, 8, 10, 12, 14, 16, 18, 3, 6, 9, 12, 15, 18, 21, 24, 27, 4, 8, 12, 16, 20, 24, 28, 32, 36, 5, 10, 15, 20, 25, 30, 35, 40, 45, 6, 12, 18, 24, 30, 36, 42, 48, 54, 7, 14, 21, 28, 35, 42, 49, 56, 63, 8, 16, 24, 32, 40, 48, 56, 64, 72, 9, 18, 27, 36, 45, 54, 63, 72, 81]

# 두 줄로 쓸 수도 있다.
a = [i * j for j in range(2, 10)
           for i in range(1, 10)]
```

![Image](/assets/postimage/listcomprehension_2.png){:.border}

<br>
#### 이외 파이썬에서 자주 쓰이는 것! (계속 작성 예정)
(1) 리스트
<br>
(2) ...

<br>
<h2 id="h4">출처</h2>
[파이썬 코딩도장](https://dojang.io/course/view.php?id=7)