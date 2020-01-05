---
layout: post
title: docker setting
category:
    - infra

---

## Container to image
---
```
docker commit [container name] [targer image name]
ex) docker commit websver webserver

docker image에 태그 달기

docker tag [image name] [user_id]/[tag]
```
## Docker push
---

* docker login
```
docker login 커맨드 실행
```

*docker push
```
docker push blue32x/myblog:tagname 명령어 실행
```
