---
layout:     post
title:      archlinux配置记录
subtitle:   系统中的战斗机
date:       2021-04-16
author:     Glider
header-img: img/幻想.jpg
catalog: true
tags:
    - archlinux
    - 树莓派
---

# 前言

其实老早就听说过这个linux版本了，也装过几次（不过最后都崩了）。

今天因为要在树莓派上使用bcache，而raspbian系统里面是没有这个内核的……索性采用archlinux试试 (bcache太久没人维护了，所以换成lvm cache了，感觉还行)

所以这篇文章的操作对象是树莓派4b，其他版本可以借鉴。

# 正文

## 系统安装
国内有系统镜像：http://mirrors.ustc.edu.cn/

在里面可以找到4b对应的系统版本 http://mirrors.ustc.edu.cn/archlinuxarm/os/ArchLinuxARM-rpi-4-latest.tar.gz

系统刷写方法需要全程在linux中进行（可能win上有可以用的软件？）

所以找了隔壁组的老哥借了一个8g的sd卡，刷成raspbian系统，然后再在raspbian中挂载读卡器，把原来那张sd卡刷成arch……

这是官方安装教程：https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-4

> 注意：此安装过程最好全程使用root用户，并且工作目录也在root根目录下
> ps：关于换源的问题，在校园网的环境下，个人觉得挺快的，所以没有换，各位老哥可以看情况对软件源进行更改

> 注意，arch装完后ssh进入，接下来的操作最好是在root用户下，不然可能又出什么弔问题……

## 系统初始化

换源：

`vi /etc/pacman.d/mirrorlist`

```
#清华
Server = http://mirrors.tuna.tsinghua.edu.cn/archlinuxarm/$arch/$repo
# 中科大
Server = http://mirrors.ustc.edu.cn/archlinuxarm/$arch/$repo
#成都电子科大
Server = http://mirrors.stuhome.net/archlinuxarm/$arch/$repo
```

`pacman -Syyu  #刷新`

安装AUR构建工具：`pacman -S --needed base-devel`

安装git：`pacman -S git`


## docker安装

学了docker之后，啥系统都想装docker爽爽，arch当然也不例外

docker在arch的官方包管理器pacman中有，所以安装挺方便的

root用户执行：`pacman -S docker`  

装完后换docker镜像源：

```
pacman -S vim  #安装vim

mkdir /etc/docker

tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["xxxxxxx"]   #这里的xxxx是docker镜像，根据需要换成对应的链接
} 
EOF

systemctl daemon-reload

systemctl restart docker

systemctl enable docker #设置开机自启

reboot #重启
```


docker安装好之后，现在只能在root时使用，如果要在普通用户也能使用的话，方式如下：

```
pacman -S sudo #root执行

visudo #把 %wheel ALL=(ALL) ALL 这行前面的注释去掉

su alarm # 切换回普通用户

sudo gpasswd -a ${USER} docker #添加用户

sudo systemctl restart docker  #docker 重启

```

