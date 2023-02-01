---
title: 별 찍기 - 10(백준 2447번) 풀이 방법 정리
tags: Algorithm_Solution
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

별 찍기 - 10(백준 2447번) 문제의 여러 가지 풀이 방법에 대해 정리해 보았다

<!-- more -->
<h2 id="h1">별 찍기 - 10</h2>
크기 3의 패턴은 가운데에 공백이 있고, 가운데를 제외한 모든 칸에 별이 하나씩 있는 패턴이다. N이 3보다 클 경우, 크기 N의 패턴은 공백으로 채워진 가운데의 (N/3)×(N/3) 정사각형을 크기 N/3의 패턴으로 둘러싼 형태이다. N=3<sup>k</sup>이며, 이때 1 ≤ k < 8 이다.

문제 : [별 찍기 - 10](https://www.acmicpc.net/problem/2447)

<h2 id="h2">재귀 없이 해결하는 방법</h2>
별이 찍히지 않는 곳의 좌표는 3으로 계속 나누면 나머지로 (1, 1)이 남는다는 규칙이 있다. <br>
이 규칙에 따라 좌표 값을 계속 3으로 나눠 가며 (1, 1)이 남는지 확인한다.

```cpp
// 좌표(x, y) 값을 3으로 나누어 보았을 때  
// 마지막에 1, 1이 남으면 그 부분은 공백이다.

#include <cstdio>

int star(int x, int y);

int main(void) {
    int number = 0, x = 0, y = 0;

    scanf("%d", &number);

    for (x = 0; x < number; x++) {
        for (y = 0; y < number; y++) {
            if ( star(x, y) ) printf(" ");
            else printf("*");
        }
        printf("\n");
    }
    return 0;
}

int star(int x, int y) {
    while (1) {
        if ( ( (x % 3) == 1 ) && ( ( y % 3 ) == 1 ) ) return 1;
        if ( x == 0 || y == 0 ) return 0;
        x = x / 3;
        y = y / 3;
    }
}
```

<h2 id="h3">재귀로 해결하는 방법(1)</h2>
위 규칙에 따라 별이 찍히지 않는 곳의 좌표를 재귀함수로 구현하면 다음과 같다.

```cpp
// 좌표(x, y) 값을 3으로 나누어 보았을 때 
// 마지막에 1, 1이 남으면 그 부분은 공백이다.

#include <cstdio>

int blank(int x, int y)
{
    if ( ( ( x % 3 ) == 1 ) && ( ( y % 3 ) == 1 ) )
    {
        return 1;
    }
    else if ( x == 0 || y == 0 )
    {
        return 0;
    }
    else
    {
        x = x / 3;
        y = y / 3;
        return blank(x, y);
    }
}

int main(void) {
    int number = 0, x = 0, y = 0;

    scanf("%d", &number);

    for (x = 0; x < number; x++) {
        for (y = 0; y < number; y++) {
            if ( blank(x, y) ) printf(" ");
            else printf("*");
        }
        printf("\n");
    }
    return 0;
}
```

<h2 id="h4">재귀로 해결하는 방법(2)</h2>
별 표시 여부를 표시하는 배열을 먼저 선언한 후, 재귀함수를 이용하여 맨 왼쪽 3x3 부분부터 시작하여 오른쪽으로 차례로 채워 나간다.

```python
# 재귀 : 큰 케이스로부터 기본 케이스까지 들어간다.
# 1. base 케이스 : 3x3
# 2. 재귀 : 가운데 부분을 비워두고 나머지 부분을 3x3, 9x9... 등 기본 모양으로 채운다.
# 3. 맨 왼쪽 3x3 부터 채우고 => 맨 왼쪽 9x9부터 채우고 => 맨 왼쪽 27x27부터 채우고... 의 반복

import sys
sys.setrecursionlimit(10**6)	# 파이썬 재귀 제한 늘리기

def paint_star(LEN):
    DIV3 = LEN//3
    if LEN == 3:
        g[1] = ['*', ' ', '*']
        g[0][:3] = g[2][:3] = ['*']*3
        return

    paint_star(DIV3)

    for i in range(0, LEN, DIV3):
        for j in range(0, LEN, DIV3):
            if i != DIV3 or j != DIV3:
                for k in range(DIV3):
                    g[i+k][j:j+DIV3] = g[k][:DIV3]

n = int(sys.stdin.readline().strip())
g = [[' ' for _ in range(n)] for _ in range(n)]
paint_star(n)

for i in range(n):
    for j in range(n):
        print(g[i][j], end='')
    print()
```