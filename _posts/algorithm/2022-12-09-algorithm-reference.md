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
<h2 id="h1">C언어/C++</h2>
#### - 배열 초기화에는 memset() 함수를 활용한다.
```cpp
#include <memory.h> 또는
#include <string.h>

// 매개변수 : 배열 이름, 초기화할 값, 바이트 단위의 초기화할 영역 크기
void * memset ( void * ptr, int value, size_t num );
```

<br>
<span style="color: red; font-weight: bold">※ memset 함수를 사용할 때 주의해야 할 점</span>
<br>
1) 1 Bytes 변수( char, unsigned char 등 )를 제외한 변수를 초기화 할 때는 0 이외의 값으로 초기화를 하면 안 된다.
```cpp
// 이 코드의 경우 Byte 단위로 처리가 되어
// n = [00000001000000010000000100000001] = 16843009의 원하지 않는 값으로 초기화가 된다.
int n;
memset(&n, 1, sizeof(int));
```

<br>
2) new, malloc 등을 이용하여 동적으로 배열을 생성하는 변수가 있는 struct, class에서는 memset으로 초기화를 하면 안 된다.
```cpp
// sizeof(A)는 struct member alignment가 어떤 값이든 4(int i) + 4(char* c, address는 4) = 8 Bytes가 된다.
// 그러므로 위의 소스는 동적으로 생성한 변수는 초기화가 되지 못하고, char* c가 NULL로 초기화가 되어
// 이전에 생성한 메모리는 메모리 누수가 발생하게 된다.
struct A
{
   int i;
   char* c;
};

void main()
{
   A a;
   a.c = new char[100];
   memset(&a, 0, sizeof(A));
   if(a.c != NULL)
   {
      delete[] a.c;
      a.c = NULL;
   }
}
```

```cpp
// 위와 같이 동적으로 생성하는 경우는 아래와 같이 각각을 분리하여 초기화를 해야 한다.
a.i = 0;
memset(a.c, 0, sizeof(char)*100);
```

<br>
3) CString은 절대 memset으로 초기화를 하면 안 된다.
<br>
=> CString은 내부적으로 m_pchData 변수를 동적으로 생성하여 문자열을 저장한다.
<br>이 변수에 대한 직접적인 접근은 private로 막혀 있다.
<br>그래서 CString, 또는 CString을 member variable을 가지고 있는
struct, class를 memset을 이용하여 초기화를 하면 안 된다.
CString을 memset으로 초기화를 하면 메모리 누수뿐만 아니라, run-time error도 발생한다.

<br>
4) virtual function을 가지고 있는 struct, class에서는 절대 memset으로 초기화를 하면 안 된다.
<br>
=> 실제 실행될 함수의 주소를 가리키는 공간(4 Bytes)을 추가로 가지게 되므로, virtual function이 NULL로 바인딩되어 실행할 수 없게 된다.

<br>
<h2 id="h2">파이썬</h2>
#### - 파이썬에서 재귀를 사용하여 문제를 해결할 때는 다음 코드를 사용한다.
=> 파이썬의 기본 재귀 깊이 제한은 1000으로 매우 얕은 편이기 때문에, 재귀로 알고리즘 문제를 풀 경우 자주 이 제한에 걸리게 된다.

```python
import sys
sys.setrecursionlimit(10 ** 6)
```

<br>
#### - 파이썬에서 리스트를 만들 때는 리스트 컴프리헨션(list comprehension)을 자주 쓰게 된다.
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
<h2 id="h3">출처</h2>
[memset 함수 사용 시 주의사항](https://shaeod.tistory.com/282) <br>
[파이썬 코딩도장](https://dojang.io/course/view.php?id=7)