---
title: Java
date: 2021-12-15 23:58:01
tags:
 - Java

---

Created: 2021-12-15 23:58:01

Modified: 2021-12-15 23:58:01

<!--more-->

# jdk

refer to https://blog.csdn.net/hty1053240123/article/details/52504952 and https://developer.aliyun.com/article/704959.

```bash
getconf LONG_BIT

java --version
whereis java

cd Downloads
sudo mkdir /usr/java
sudo tar -zxvf jdk-8u291-linux-x64.tar.gz -C /usr/java/

cd  /usr/java/
sudo mv jdk1.8.0_291 jdk_8u291
sudo gedit ~/.bashrc
source ~/.bashrc
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/java/jdk_8u291/bin/java" 300
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/java/jdk_8u291/bin/javac" 300
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/java/jdk_8u291/bin/javaws" 300
sudo update-alternatives --install /usr/bin/jar jar /usr/java/jdk_8u291/bin/jar 300
sudo update-alternatives --install /usr/bin/javah javah /usr/java/jdk_8u291/bin/javah 300
sudo update-alternatives --install /usr/bin/javap javap /usr/java/jdk_8u291/bin/javap 300
sudo update-alternatives --config java
java -version
sudo update-alternatives --config javac
```

`~/.bashrc`:

```bash
#set oracle jdk environment
export JAVA_HOME=/usr/java/jdk_8u291  ## 这里要注意目录要换成自己解压的jdk 目录
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH

```

