---
title: ChatGPT-Midjourney
date: 2023-06-15T12:15:23+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1684093025838-b6f9ec4fb570?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODY4MDI0OTd8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1684093025838-b6f9ec4fb570?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODY4MDI0OTd8&ixlib=rb-4.0.3
---

# [Licoy/ChatGPT-Midjourney](https://github.com/Licoy/ChatGPT-Midjourney)

<div align="center">

<h1 align="center">ChatGPT-Midjourney</h1>

中文 | [English](./README_EN.md) | [日本語](./README_JA.md)

一键免费部署你的私人 ChatGPT+Midjourney 网页应用（基于[ChatGPT-Next-Web](https://github.com/Yidadaa/ChatGPT-Next-Web)开发）

[QQ交流群](http://qm.qq.com/cgi-bin/qm/qr?_wv=1027&k=gAGpNxOKdRB3L_IiHWAfT4MUQzgBOor-&authKey=Ty8WQgZFub8W1EsG3LQE2B3xxRRBzD0Rj1rPyRVFdT6IqnJgGcpPZB5l8ZVJTB1n&noverify=0&group_code=849273126) | [Telegram群组](https://t.me/gptmj) | [全平台AI智能助手](https://dd.gitcdn.top/Atop)

[![Deploy with Vercel](https://img.shields.io/badge/Vercel-部署-00CCCC.svg?logo=vercel)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FLicoy%2FChatGPT-Midjourney&env=OPENAI_API_KEY&env=MIDJOURNEY_PROXY_URL&env=CODE&project-name=chatgpt-midjourney&repository-name=ChatGPT-Midjourney)
[![Deploy with Railway](https://img.shields.io/badge/MidjourneyProxy-Railway部署-009900.svg?logo=railway)](https://github.com/novicezk/midjourney-proxy/blob/main/docs/railway-start.md)

[![WordPress+ChatGPT支持](https://img.shields.io/badge/WordPress-ChatGPT%20部署-red.svg?logo=wordpress&logoColor=red&style=for-the-badge)](https://github.com/Licoy/wordpress-theme-puock)

![主界面](./docs/images/cover.png)

</div>

## 功能支持
- [x] 原`ChatGPT-Next-Web`所有功能
- [x] midjourney `imgine` 想象
- [x] midjourney `upscale` 放大
- [x] midjourney `variation` 变幻
- [x] midjourney `describe` 识图
- [x] midjourney `blend` 混图
- [x] midjourney 垫图
- [x] 绘图进度百分比、实时图像显示
- [ ] 自身支持midjourney-api

## 参数说明
### MIDJOURNEY_PROXY_URL
```shell
MIDJOURNEY_PROXY_URL=http://yourip:port
```
> ⚠️注意：如果你使用的是Docker部署，那么这里的地址应该是`http://公网IP:port`，而不是`http://localhost:port`，因为Docker中的容器是隔离的，`localhost`指向的是容器内部的地址，而不是宿主机的地址。
- 界面中

![mj-6](./docs/images/mj-6.png)

### MIDJOURNEY_PROXY_API_SECRET
（可选）`midjourney-proxy`的API请求密钥，防止他人恶意调用，可在环境变量中配置。

### CODE
（可选）设置页面中的访问密码，防止被其他人轻易使用消耗余额

## 部署
### ChatGPT-Midjourney 前端部署
#### Docker
```shell
docker pull licoy/chatgpt-midjourney:v1.3.2
docker run -d -p 3000:3000 \
   -e OPENAI_API_KEY="sk-xxx" \
   -e CODE="123456" \
   -e BASE_URL="https://api.openai.com" \
   -e MIDJOURNEY_PROXY_URL="http://ip:port" \
   licoy/chatgpt-midjourney:v1.3.2
```
#### Vercel
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FLicoy%2FChatGPT-Midjourney&env=OPENAI_API_KEY&env=MIDJOURNEY_PROXY_URL&env=CODE&project-name=chatgpt-midjourney&repository-name=ChatGPT-Midjourney)
#### Zeabur

##### Zeabur介绍

1. `Railway` 更新机制后，只允许注册使用超过半年的 `Github` 账户部署服务 

2. 通过 `Vercel` 和 `Railway` 部署的项目会自动生成一个域名

3. 然而因为某些原因，形如 `*.vercel.app` 和 `*.up.railway.app` 的域名在国内无法访问

4. 但是你可以通过购买自己的域名来解析 `CNAME` 达到国内可访问的效果

5. 但是如果你只想白嫖，一分钱不想花，那么你就可以用 `Zeabur` 了

6. `Zeabur` 服务器运行在国外，但是其生成的域名没有被污染，也就是说，你不需要绑定自己的域名了

##### 开始部署

打开网址

[Zeabur：https://zeabur.com](https://zeabur.com/zh-CN)

点击现在开始

点击 `Sign in with GitHub`

登陆你的 `Github` 账号

点击 `Authorize zeabur` 授权

点击 `创建项目` 并输入一个项目名称，点击 `创建`

点击 `+` 添加服务，选择 `Git-Deploy service from source code in GitHub repository.`

点击 `Configure GitHub` 根据需要选择 `All repositories` 或者 `Only select repositories`

点击 `install`,之后自动跳转，最好再刷新一下页面

点击 你 fork 的 `ChatGPT-Midjourney` 项目

点击环境变量，添加你需要的环境变量

然后取消 `Building`，点击 `Redeploy` (此做法是为了让环境变量生效)

部署 `ChatGPT-Midjourney` 大概需要 `6` 分钟，此时你可以做的是：配置域名

点击下方的域名，点击生成域名，输入前缀，例如我的是 `chatgpt-midjourney.zeabur.app`，点击保存

或者也可添加自定义域名，之后加上 `CNAME` 解析即可

等待部署成功即可

#### 手动部署
- clone本项目到本地
- 安装依赖
```shell
npm install
npm run build
npm run start // #或者开发模式启动： npm run dev
```
### midjourney-proxy 服务部署
#### Docker
- 运行 `midjourney-proxy` (Midjourney API服务，更多参数配置可以参考：[midjourney-proxy](https://github.com/novicezk/midjourney-proxy))
```shell
docker pull novicezk/midjourney-proxy:2.1.6
docker run -d --name midjourney-proxy \
 -p 8080:8080 \
 -e mj.discord.guild-id=xxx \
 -e mj.discord.channel-id=xxx \
 -e mj.discord.user-token=xxx \
 -e mj.discord.bot-token=xxx \
 --restart=always \
 novicezk/midjourney-proxy:2.1.6
```
#### Railway
> Railway是一个提供弹性部署方案的平台，服务在海外，方便MidJourney的调用。

参考：[midjourney-proxy - Railway 部署教程](https://github.com/novicezk/midjourney-proxy/blob/main/docs/railway-start.md)

#### Zeabur 

> Zeabur 部署在海外，对于新注册的 `Github` 账号来说，使用不了 `Railway`，但是能用 `Zeabur`

##### 开始部署

打开网址

[Zeabur：https://zeabur.com](https://zeabur.com/zh-CN)

点击现在开始

点击 `Sign in with GitHub`

登陆你的 `Github` 账号

点击 `Authorize zeabur` 授权

点击 `创建项目` 并输入一个项目名称，点击 `创建`

点击 `+` 添加服务，选择 `Git-Deploy service from source code in GitHub repository.`

点击 `Configure GitHub` 根据需要选择 `All repositories` 或者 `Only select repositories`

点击 `install`,之后自动跳转，最好再刷新一下页面

点击 你 fork 的 `midjourney-proxy` 项目

点击环境变量，点击编辑原始环境变量，添加你需要的环境变量

关于环境变量，与 `Railway` 稍有不同，需要把 `.` 和 `-` 全部换成 `_`，例如如下格式

```
PORT=8080
mj_discord_guild_id=xxx
mj_discord_channel_id=xxx
mj_discord_user_token=xxx
```

然后取消 `Building`，点击 `Redeploy` (此做法是为了让环境变量生效)

部署 `midjourney-proxy` 大概需要 `2` 分钟，此时你可以做的是：配置域名

点击下方的域名，点击生成域名，输入前缀，例如我的是 `midjourney-proxy.zeabur.app`，点击保存

注意此时的域名就是你的 `MIDJOURNEY_PROXY_URL` 

不要再加端口，例如 `https://midjourney-proxy.zeabur.app`,而不是 `https://midjourney-proxy.zeabur.app:port`

或者也可添加自定义域名，之后加上 `CNAME` 解析即可

等待部署成功即可

## 使用
在输入框中以`/mj`开头输入您的绘画描述，即可进行创建绘画，例如：
```
/mj a dog
```
### 混图、识图、垫图
![mj-5](./docs/images/mj-5.png)
> 提示：垫图模式/识图(describe)模式只会使用第一张图片，混图(blend)模式会按顺序使用选中的两张图片（点击图片可以移除）

## 截图
### 混图、识图、垫图
![mj-4](./docs/images/mj-4.png)
### 状态实时获取
![mj-2](./docs/images/mj-1.png)
### 自定义midjourney参数
![mj-2](./docs/images/mj-2.png)
### 更多功能
- 等你自行发掘

## 鸣谢
- [ChatGPT-Next-Web](https://github.com/Yidadaa/ChatGPT-Next-Web)
- [midjourney-proxy](https://github.com/novicezk/midjourney-proxy)

## 开源协议
[Anti 996 LICENSE](./LICENSE)
