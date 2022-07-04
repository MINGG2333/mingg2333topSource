---
title: Windows
date: 2021-8-2 10:59:57
tags: 
 - Windows

---

<!--more-->

# command line

```bash
set PATH_TO_BERT=1
echo %PATH_TO_BERT%

cls

python run_cmrc2018_drcd_baseline.py ^
    --use_tpu=False
```

`Esc`: clear line

`Ctrl + C`: cancel the command lines

## port

```shell
netstat -ano
netstat -aon|findstr 2018
```

## pid

```bash
tasklist | findstr 50264
tasklist | findstr simulator.exe

taskkill /f /t /pid 9088 
taskkill /f /t /im simulator.exe
```

# proxy

```shell
# CMD
set http_proxy=http://127.0.0.1:7890
set https_proxy=http://127.0.0.1:7890
set http_proxy=
set https_proxy=
# Git Bash
git config --global https.proxy http://127.0.0.1:7890
git config --global https.proxy https://127.0.0.1:7890
git config --global http.proxy 'socks5://127.0.0.1:7891' 
git config --global https.proxy 'socks5://127.0.0.1:7891'
git config --global --unset http.proxy
git config --global --unset https.proxy
# PowerShell, not necessary
$env:http_proxy="http://127.0.0.1:7890"
$env:https_proxy="http://127.0.0.1:7890"
```
