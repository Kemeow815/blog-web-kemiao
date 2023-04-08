---
title: chatchan-dist
date: 2023-04-08T12:17:21+08:00
draft: False
featuredImage: https://wallpaperhub.app/api/v1/get/11999/0/1080p
featuredImagePreview: https://wallpaperhub.app/api/v1/get/11999/0/1080p
---

# [easychen/chatchan-dist](https://github.com/easychen/chatchan-dist)

# Chat酱独立部署版

## 默认界面

![](images/20230404174420.png)

## 最近更新

v1.0.2 

- 支持自动保存对话，支持总结对话标题

![](images/20230404174121.png)

- 支持自定义背景

![](images/20230404174028.png)


Chat酱网页版（[c.level06.com](https://c.level06.com)）部署在海外服务器，有部分同学访问不了，因此提供一个独立部署版，你可以将它部署到任何服务器，甚至在电脑直接用支持浏览本地网页的浏览器打开使用。

## 使用方法

1. 下载 [build.zip](./build.zip) 
1. 解压后，你会得到一个完整的网站，访问 index.html 即可使用，如果你的浏览器不支持查看本地网页，那么可以下载我打包这些网页的桌面客户端（ 链接：https://share.weiyun.com/jXtYKbZS 密码：chatok ）
1. 如果要给其他同学使用，可以把这个目录部署到服务器上，然后访问对应目录就行。

## Docker版

虽然我觉得静态网页更简单，但有同学表示想要docker版，于是我让GPT写了个Dockerfile，于是就有了docker版。

使用方法：

```bash
docker run -d -p 9000:9000 easychen/chatchan:latest
```

对话截图：

![](images/20230406173224.png)

