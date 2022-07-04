---
title: Zotero
date: 2021-11-4 22:49:12
tags:
 - tool
 - Zotero
 - bibliography management
---

Created: Mon Jul 12 10:19:53 CST 2021

Modified: 2021-11-4 22:49:06

<!--more-->

# Installation

Refer to [安装](https://blog.csdn.net/xinjieyuan/article/details/105407564),

```bash
sudo apt-add-repository ppa:smathot/cogscinl
sudo apt-get update
sudo apt-get install zotero-standalone
cd /opt
sudo chown -R root:root zotero/
sudo chmod 777 zotero/
cd zotero
sudo chmod -R a+rx *.desktop
sudo chown -R <user name>:<user name> *.desktop
```

or use `.deb` file

```bash
./set_launcher_icon
ln -s ~/zotero/zotero.desktop ~/.local/share/applications/zotero.desktop
```



# Configuration

Refer to [初始设定](https://zhuanlan.zhihu.com/p/31852030)

## Sync

### Dropbox

prepare a own cloud for sync, like **Dropbox**, for installation on Ubuntu refer to https://vitux.com/how-to-install-and-sync-dropbox-on-ubuntu/, https://www.mywiki.cn/hovercool/index.php/%E5%AE%89%E8%A3%85Dropbox%E5%AE%A2%E6%88%B7%E7%AB%AF, https://ywnz.com/linuxjc/5772.html.

Note: if you use proxy, you'd better to configure it manually in **Dropbox Preferences**.

Refer to [ZotFile 配合同步盘](https://zhuanlan.zhihu.com/p/31453719), [Zotero和zotfile插件关联以及使用](https://zhuanlan.zhihu.com/p/104848524).

From [zotfile offical website](https://link.zhihu.com/?target=http%3A//zotfile.com/) download `zotfile` Add-ons, then install and configure it.

![zotfileprefer](Zotero/zotfileprefer.png)

![image-20211104225200656](Zotero/image-20211104225200656.png)

![image-20211104225013898](Zotero/image-20211104225013898.png)

原理：

实体文件 虚链接 

manage attachments，rename attachments 

工具—管理附件——转换已链接文件为已存储文件



() tablet

manage attachments—send to tablet

manage attachments—get from tablet
