---
layout: post
title: 2019-11-02-Crostini修复系统语言乱码与使用Google拼音输入法
date: 2019-11-02
categories: blog
tags: [Crostini,ChromeOS]
description: none
---
## 更改系统默认语言
### 安装语言包
修改locale.gen文件

```
sudo vim /etc/locale.gen
```
去掉zh_CN.GBK GBK,zh_CN.UTF8 UTF8的注释
-使用 `sudo locale-gen`下载语言。
### 修改默认语言编码
```
sudo dpkg-reconfigure locales
```
选择系统的默认语言
## 修复中文乱码
### 安装中文字体
```
sudo apt-get install xfonts-wqy ttf-wqy-zenhei ttf-wqy-microhei
```
如果中文依然乱码尝试重启
## 安装中文输入法
### 安装Fcitx
```
sudo apt install fcitx-googlepinyin
```
### 配置Fcitx
```
im-config
```
### 添加输入法
```
fcitx-config-gtk3
```
在界面中添加谷歌拼音输入法，如果没看到尝试重启
### 设置开机自启动
```
sudo vim ~/.sommelierrc
```
添加以下内容
```
/usr/bin/fcitx-autostart
```
