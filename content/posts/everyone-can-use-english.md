---
title: everyone-can-use-english
date: 2024-01-19T12:16:47+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1703027817396-2e4a8ca87fdd?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDU2Mzc4MDB8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1703027817396-2e4a8ca87fdd?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDU2Mzc4MDB8&ixlib=rb-4.0.3
---

# [xiaolai/everyone-can-use-english](https://github.com/xiaolai/everyone-can-use-english)

# 人人都能用英语

中文 | [English](README.en-US.md)

## 目录

- [简介](./book/README.md)
- [第一章：起点](./book/chapter1.md)
- [第二章：口语](./book/chapter2.md)
- [第三章：语音](./book/chapter3.md)
- [第四章：朗读](./book/chapter4.md)
- [第五章：词典](./book/chapter5.md)
- [第六章：语法](./book/chapter6.md)
- [第七章：精读](./book/chapter7.md)
- [第八章：叮嘱](./book/chapter8.md)
- [后记](./book/end.md)

## 应用

- [Enjoy App](./enjoy/README.md)

## * 开发者

### 本地启动

```bash
yarn install
yarn start:enjoy
```

### 编译

```bash
yarn make:enjoy
```

## * 普通小白用户

方法一：这是**最直接简单的方法**是去 [releases 页面](https://github.com/xiaolai/everyone-can-use-english/tags)下载相应的安装文件。

> 如果你需要**详细下载操作指导**[点这里](find-compatible-software-version.md)


> [!TIP]
> 如果你是普通用户，并不想为本项目提供代码，按上面的操作就可以正常使用 Enjoy APP ！



方法二：如果想要随时**试用更新版本**的话，请按一下步骤操作。



### MacOS 用户

1. 打开命令行工具 Terminal

2. 安装 Homebrew（请参阅这篇文章：《[从 Terminal 开始…](https://github.com/xiaolai/apple-computer-literacy/blob/main/start-from-terminal.md)》）

3. 安装 `nodejs` 以及 `yarn`：

   ```bash
   brew install nvm
   nvm install 20.5.1 
   brew install yarn
   ```

4. 设置 yarn 环境变量以及 Node.js 配置

   ```bash
   export ELECTRON_MIRROR="https://npmmirror.com/mirrors/electron/"
   corepack enable
   ```

5. 克隆此仓库至本地，而后安装、启动：

   ```bash
   cd ~
   mkdir github
   cd github
   git clone https://github.com/xiaolai/everyone-can-use-english
   cd everyone-can-use-english
   yarn install
   yarn start:enjoy
   ```



### Windows 用户

系统要求：Windows 10 22H2 以上版本、 [Windows PowerShell 5.1](https://aka.ms/wmf5download) 以上版本、互联网网络连接正常。

1. 将鼠标移至任务栏的 “Windows 徽标” 上单击右键，选择 “PowerShell”

   > tips 1 ：在最新的 Windows 11 上，你看不到 “PowerShell” 选项，只有 “终端”
   >
   > tips 2 ：不能用管理员权限运行 PowerShell ，否则会导致 Scoop 安装失败
   >

2. 在弹出的 PowerShell 窗口中依次执行运行以下命令，安装Scoop：

   ```powershell
   # 设置 PowerShell 执行策略
   Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
   # 下载安装脚本
   irm get.scoop.sh -outfile 'install.ps1'
   # 执行安装, --ScoopDir 参数指定 Scoop 安装路径
   .\install.ps1 -ScoopDir 'C:\Scoop'
   ```

   如果出现下面的错误：

   > <span style="color:red">irm : 未能解析此远程名称: 'raw.githubusercontent.com'</span>

   说明你的**网络连接**有问题，请自行研究解决：

3. 安装 Nodejs 和 yarn 以及其他依赖环境 ：

   ```powershell
   scoop install nodejs
   scoop install git
   npm install yarn -g
   ```

4. 设置 yarn 环境变量以及 Node.js 配置

   ```powershell
   $env:ELECTRON_MIRROR="https://npmmirror.com/mirrors/electron/"
   corepack enable
   ```

5. 克隆此仓库至本地，而后安装 Enjoy APP：

   ```powershell
   cd ~
   mkdir github
   cd github
   git clone https://github.com/xiaolai/everyone-can-use-english
   cd everyone-can-use-english
   yarn install
   ```

   出现 `“YN0000: · Done …… ” ` 类似字样说明安装成功！

6. 运行 Enjoy APP ，在终端执行下列命令：

   ```powershell
   yarn start:enjoy
   ```



## 更新Enjoy

更新并使用最新版本的Enjoy：

1. 将仓库最新内容拉取到本地，在命令行工具中执行：

   ```bash
   git pull
   ```
   结果显示为：

   ```shell
   Already up to date.
   ```

   若非如此，那么意味着代码有所更新，那么就要运行以下命令：

   ```bash
   yarn install
   ```

2. 运行Enjoy APP：

   ```shell
   yarn start:enjoy
   ```
