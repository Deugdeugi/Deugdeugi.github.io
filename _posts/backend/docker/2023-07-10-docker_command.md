---
title: Docker 명령어 목록
tags: Docker
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

Docker 명령어 목록을 정리해 보았다

<!-- more -->

## docker 버전 표시
```
docker -v
```

## docker 데몬 실행
```
dockerd &
```

## MAC에서 docker 데몬 실행 관련 참고 글
[https://godtaehee.tistory.com/m/35?category=976391](https://godtaehee.tistory.com/m/35?category=976391)

## Window에서 WSL 실행 안 될 때
[https://hbase.tistory.com/291](https://hbase.tistory.com/291)

## docker 이미지 관련 명령어
```
1) 현재 이미지 목록 : docker image ls

2) 이미지 삭제 : docker image rm (이미지명)

3) 이미지로 컨테이너 생성 : docker run -v (외부 저장소 작업 디렉토리 경로):(docker 내부 경로) --name (컨테이너 이름) -p 22:22 -itd (이미지 이름) --privileged
(ex) docker run -v /Users/hooramseo/project/docker/work:/root/work --name accountapp -p 22:22 -itd ubuntu:18.04
```
※ run 명령어 옵션 참조 : [https://wooono.tistory.com/348](https://wooono.tistory.com/348)  
※ docker privileged 옵션 관련 오류 : [https://stackoverflow.com/questions/72695311/failure-starting-docker-container-failed-to-create-shim-task-oci-runtime-crea](https://stackoverflow.com/questions/72695311/failure-starting-docker-container-failed-to-create-shim-task-oci-runtime-crea)  
※ docker 내부 권한 문제 발생 : [https://engineer-mole.tistory.com/264](https://engineer-mole.tistory.com/264)  

## docker 컨테이너 관련 명령어
```
1) 컨테이너 실행 : docker run -itd (이미지명):(태그명)

2) 실행 중인 컨테이너 목록 보기 : docker ps -a

3) 컨테이너 멈추기 : docker stop (컨테이너 ID)

4) 컨테이너 시작하기 : docker container start (컨테이너 ID)

5) 컨테이너 삭제하기 : docker container rm (컨테이너 ID)

6) 컨테이너 진입 : docker exec -it (컨테이너 이름 or ID) /bin/bash
```

## docker 컨테이너로 이미지 만들기
```
1) 컨테이너의 현재 상태 이미지로 생성 : docker commit -a "(author 정보)" -m "(commit message)" (컨테이너 이름) (만들 이미지 이름):(만들 태그 이름)

2) Docker Hub Login : docker login

3) Docker Hub에 이미지 업로드 : docker image push <docker ID/Image name:tag>

4) 태그 이름 변경 : docker image tag [다시 태그 할 이미지] [새 태그 명]

5) Docker Hub에서 이미지 불러오기 : docker image pull (이미지 이름):(태그 이름)
```

※ root 권한 상태로 Docker Hub에 로그인이 되지 않는 현상이 있음... 왜 그런지는 알아봐야 함  
※ Docker Hub에 로그인 한 ID와 이미지의 유저 ID가 다른 경우 push가 되지 않는다. : [https://velog.io/@eunsilson/Docker-Docker-Hub-push-%EC%8B%A4%ED%8C%A8-requested-access-to-the-resource-is-denied](https://velog.io/@eunsilson/Docker-Docker-Hub-push-%EC%8B%A4%ED%8C%A8-requested-access-to-the-resource-is-denied)  
(ex) 이미지 이름을 (Docker Login ID)/(임의의 이름):(태그 이름) 으로 구성해야 push가 된다.

## Docfile을 이용하여 이미지 생성
[https://javacan.tistory.com/entry/docker-start-7-create-image-using-dockerfile](https://javacan.tistory.com/entry/docker-start-7-create-image-using-dockerfile)

## 출처
- [docker run 옵션 참조](https://wooono.tistory.com/348)  
- [docker privileged 옵션 관련 오류](https://stackoverflow.com/questions/72695311/failure-starting-docker-container-failed-to-create-shim-task-oci-runtime-crea)  
- [docker 내부 권한 문제 발생](https://engineer-mole.tistory.com/264)  
- [docker 컨테이너로 이미지 만들기](https://yoo11052.tistory.com/144)  
- [docker 이미지 push](https://honggg0801.tistory.com/21)  
- [docker 이미지 push 오류가 날 때는?](https://velog.io/@eunsilson/Docker-Docker-Hub-push-%EC%8B%A4%ED%8C%A8-requested-access-to-the-resource-is-denied)  
- [docker 이미지 불러오기](https://ahniverson.tistory.com/24)  
- [Docfile을 통한 이미지 생성](https://javacan.tistory.com/entry/docker-start-7-create-image-using-dockerfile)
