---
title: Docker
date: 2022-1-16 01:12:24
tags:
 - Docker



---

Created: 2022-1-16 01:12:24

Modified: 2022-1-16 01:12:24

<!--more-->

# quick use

```bash
# Command used outside container
# image
docker images
docker search ubuntu
docker pull ubuntu:15.10
docker pull training/webapp
docker rmi hello-world
docker tag 860c279d2fec runoob/centos:dev
docker commit -m="has update" -a="runoob" e218edb10161 runoob/ubuntu:v2 # ?
# container
docker run -t -i ubuntu:15.10 /bin/bash # run create new container, ubuntu is a 'image name'
docker run -itd --name ubuntu-test ubuntu:15.10 /bin/bash # '-d' means running in background
docker run -d -P training/webapp python app.py # random port of host -> port of container
docker run -d -p 5000:5000 training/webapp python app.py # 5000 -> 5000
docker start b750bbbcfd88 # b750bbbcfd88 is a 'container id'
docker stop b750bbbcfd88
docker restart b750bbbcfd88
docker exec -it b750bbbcfd88 /bin/bash # enter container that running in background
docker rm -f b750bbbcfd88
docker container prune # clean all that exited

docker ps -a
docker port b750bbbcfd88
docker port ubuntu-test
docker logs -f bf08b7f2cd89 # Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
docker top ubuntu-test # PID, ...
docker inspect ubuntu-test # detaied config and state

sudo gpasswd -a $USER docker
newgrp docker
reboot
```

# what it is

two concepts: container, image

image: store sth. 

container: load image

refer to: https://www.runoob.com/docker/docker-image-usage.html

# How to build a image

refer to https://www.runoob.com/docker/docker-image-usage.html

1. create a Dockerfile in /Documents

```
FROM    centos:6.7
MAINTAINER      Fisher "fisher@sudops.com"

RUN     /bin/echo 'root:123456' |chpasswd
RUN     useradd runoob
RUN     /bin/echo 'runoob:123456' |chpasswd
RUN     /bin/echo -e "LANG=\"en_US.UTF-8\"" >/etc/default/local
EXPOSE  22
EXPOSE  80
CMD     /usr/sbin/sshd -D
```

2. build 

```bash
docker build -t runoob/centos:6.7 /Documents
```

# Commit

refer to https://yeasy.gitbook.io/docker_practice/image/commit.
