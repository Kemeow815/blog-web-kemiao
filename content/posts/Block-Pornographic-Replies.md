---
title: Block-Pornographic-Replies
date: 2023-07-01T12:16:45+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1687186735445-df877226fae9?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODgxODQ5ODN8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1687186735445-df877226fae9?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODgxODQ5ODN8&ixlib=rb-4.0.3
---

# [slarkvan/Block-Pornographic-Replies](https://github.com/slarkvan/Block-Pornographic-Replies)

### 背景

实在受不了推文下无休无止的回复引流的黄推了，里面甚至涉及诈骗等灰产。

如果我不曾会技术，遇到这种情况，我可能是无奈。

但是我如果幸好会一点技术，还熟视无睹，无动于衷，那是我的无能。

Saving one person is saving the whole world.

### 设计宗旨

1. 隐私优先。本插件纯客户端代码，无服务端 api 或前端监控等设计

### 使用方式

1. 进入 [chrome://extensions/](chrome://extensions/)，打开「开发者模式」

2. 把代码包下载解压拖到里面即可


### 效果

目前一定得**自己装了插件才有用。且只针对推文回复下的黄推**。插件有 3 种功能。

1.标记推文回复下的黄推引流，并在自身浏览时隐藏

<img src="./misc/demo.png" alt="Image" width="300" height="400">

2. 一键批量屏蔽

<img src="./misc/how-to-block.png" alt="Image" width="600" height="209">

3. 单个屏蔽

<img src="./misc/product-demo.png" alt="Image" width="600" height="402">

具体可以拿**立党**的推文 https://twitter.com/lidangzzz/status/1674952135690027010 检测下

### 说明

原理采用的是内置的「关键词匹配」检测是否是黄推，然后进行浏览器样式上的隐藏，识别准确率大约 90%，会有少少部分的错判和漏判。可以通过点击「移出列表」按钮加入信任白名单。支持批量屏蔽，单个屏蔽。

### 后续计划

- [ ] 增加 on/off 配置
- [x] 增加一键 block 功能
- [ ] 适配 firefox 浏览器
- [ ] 进入 Store
- [ ] 其他

### 欢迎 PR
1. 想 PR 前，可以现在 discuss or issue 大概说下要做的内容

### License

MIT
