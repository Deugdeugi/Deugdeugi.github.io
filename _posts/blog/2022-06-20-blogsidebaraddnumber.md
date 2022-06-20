---
title: 블로그 왼쪽 메뉴의 항목 옆에 게시글 수가 나오도록 해 보자
tags: 공작소
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

블로그 왼쪽 메뉴를 보다가 문득 같은 카테고리의 글 개수를 옆에 표시하면 좋겠다는 생각이 들었당

<!-- more -->

<h2 id="h1">1. 어떻게 만들지?</h2>
1) jekyll에서 사용하는 변수 중에 뭔가가 있을 것 같아 찾아보니 <span style="color:red; font-weight:bold">site.tags</span> 요 변수를 사용할 수 있을 것 같다.  
2) 이걸 가지고 어떻게 하면 만들 수 있지 않을까?

<h2 id="h2">2. 그런데... (1)</h2>
1) toc.html에서 site.tags를 직접 찍어보려고 하니까 엄청난 렉이... sidebar 구조가 반복적으로 뭔가를 만드는 구조라 그런가 싶다.  
2) 그래서 for문을 통해 찍으니까 잘 찍힌다! ( for tag in site.tags )

<h2 id="h3">3. 그런데... (2)</h2>
1) 이제 태그 값이랑 비교하려고 보니... child의 속성 값 중에 비교할 값이 없네?  
2) 그래서 navigation.yml의 왼쪽 사이드바 정의에 tag 값을 추가하여 비교하도록 했다.

<h2 id="h4">4. 그런데... (3)</h2>
1) 이제 태그 항목 별 개수만 구하면 끝인데... for문 돌리는 거 말고 구할 수가 없네?  
2) 그럼 변수 하나 지정하고 for문 도는 동안 1씩 늘리면 되지롱~  
3) 이렇게 해서 구한 개수를 태그 이름 옆에 표시하면 완성!

<h2 id="h5">5. 참조</h2>
- 결과는 toc.html과 navigation.yml 파일 참조  
- 참조 링크  
(1) [https://daehopark.tistory.com/entry/Jekyll-Tag-Archive-페이지-개발](https://daehopark.tistory.com/entry/Jekyll-Tag-Archive-페이지-개발)  
(2) [https://stackoverflow.com/questions/24174401/shopify-counts-per-tags](https://stackoverflow.com/questions/24174401/shopify-counts-per-tags)  
(3) [https://stackoverflow.com/questions/48529507/jekyll-show-post-count-for-sub-categories#](https://stackoverflow.com/questions/48529507/jekyll-show-post-count-for-sub-categories#)  