---
title: tl-rtc-file
date: 2023-08-06T12:16:52+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1688380303885-c45db2972da7?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTEyOTUyNDF8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1688380303885-c45db2972da7?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTEyOTUyNDF8&ixlib=rb-4.0.3
---

# [tl-open-source/tl-rtc-file](https://github.com/tl-open-source/tl-rtc-file)

# tl-rtc-file-tool   【始于文件传输，不止于文件传输】

[![](https://img.shields.io/badge/webrtc-p2p-blue)](https://webrtc.org.cn/)
[![](https://img.shields.io/badge/code-simple-green)](https://github.com/iamtsm/tl-rtc-file/)
[![](https://img.shields.io/badge/large%20file-support-green)](https://github.com/iamtsm/tl-rtc-file/)
[![](https://img.shields.io/badge/deployment-private-yellow)](https://github.com/iamtsm/tl-rtc-file/)
[![](https://img.shields.io/badge/platform-unlimited-coral)](https://github.com/iamtsm/tl-rtc-file/)

<p align="center">
<a href="https://im.iamtsm.cn/file" target="_blank">体验地址</a> ｜
<a href="https://hub.docker.com/repositories/iamtsm" target="_blank">DockerHub</a> ｜
<a href="https://github.com/tl-open-source/tl-rtc-file/blob/master/doc/README_EN.md" target="_blank">EN-DOC</a>
</p>

<p align="center">QQ群: <a href="https://jq.qq.com/?_wv=1027&k=TKCwMBjN" target="_blank">624214498 </a></p>

#### 背景 ： 20年毕设的题目相关整理出来的

#### 简介 ：（tl webrtc datachannel filetools）用webrt在web端传输文件，支持传输超大文件。

#### 优点 ： 分片传输，跨终端，不限平台，方便使用，内网不限速（局域网最高到过70多M/s），支持私有部署，支持多文件拖拽发送，网页文件预览

#### 扩展 ： 扩展了许多丰富的小功能，如本地屏幕录制，远程屏幕共享(无延迟)，远程音视频通话(无延迟)，直播(无延迟)，密码房间，oss云存储，中继服务设置，webrtc检测，webrtc统计，文字传输(群聊，私聊)，公共聊天，远程画板，AI聊天框，丰富的后台管理，实时执行日志展示，机器人告警通知等功能... 等等

## 准备 (必须步骤)

安装node-14.21.x或14.21.x以上，npm后，进入项目目录运行下面命令

    `cd svr/`

    `npm install`

首次运行/自行开发页面，用下面两个命令之一即可

    `npm run build:dev`  (如果你需要自己开发/修改前端页面，用这个命令)

    `npm run build:pro`  (不需要开发/修改前端页面，用这个命令)

## 配置websocket (必须步骤)

修改cfg.json中相应ws配置，或者wss配置

    "ws": {
        "port": 8444,    #socket 端口
        "host": "ws://域名 或者 ip:port 或者 域名:port",  #socket ip  填局域网ip/公网ip, 局域网ip只能在局域网访问，公网ip可在公网访问
    },
    "wss" : {
        "port": 8444,   #socket 端口
        "host": "wss://域名 或者 ip:port 或者 域名:port", #socket ip  填局域网ip/公网ip, 局域网ip只能在局域网访问，公网ip可在公网访问
    },

常见情况示例 : 

比如你是用ip(10.1.2.3)的形式部署socket服务，那么host就为

    ws://10.1.2.3:8444 或者 wss://10.1.2.3:8444

如果你有域名，并且配置了代理，比如a.test.com转发到本地socket服务的8444端口，那么host就为

    ws://a.test.com 或者 wss://a.test.com

如果你有域名，但是没有转发到具体的端口，比如有b.test.com:8444访问的是socket服务的8444端口，那么host就为

    ws://b.test.com:8444 或者 wss://b.test.com:8444

## 启动 (必须步骤)

启动以下两个服务, 选一种模式启动即可

http模式启动后，访问 http://你的机器ip:9092 即可

    api服务: `npm run lapi`

    socket服务 : `npm run lsocket`

https模式启动后，访问 https://你的机器ip:9092 即可

    api服务: `npm run sapi`

    socket服务 : `npm run ssocket`


## 配置turnserver (局域网非必须步骤，公网必须步骤)

目前有两种形式去生成使用turn服务的帐号密码，一种是固定帐号密码 (优先推荐)，一种是有效期帐号密码。**选一种方式即可**

ubuntu示例:

    安装coturn  `sudo apt-get install coturn`

有效帐号密码 : `docker/coturn/turnserver-with-secret-user.conf`

    1. 修改 `listening-device`, `listening-ip`, `external-ip`, `static-auth-secret`, `realm` 几个字段即可

    2. 启动turnserver 
    
    `turnserver -c  /这个地方路径填完整/conf/turn/turnserver-with-secret-user.conf`

固定帐号密码 : `docker/coturn/turnserver-with-fixed-user.conf`

    1. 修改 `listening-device`, `listening-ip`, `external-ip`, `user`, `realm` 几个字段即可

    2. 生成用户 
    
    `turnadmin -a -u 帐号 -p 密码 -r 这个地方填配置文件中的relam`

    3. 启动turnserver  
    
    `turnserver -c  /这个地方路径填完整/docker/coturn/turnserver-with-secret-user.conf`


## 配置数据库 (非必须步骤)

修改cfg.json中相应数据库配置  

    "db": {
        "open": false, #是否开启数据库, 默认关闭
        "mysql": {
            "host": "host地址",
            "port": 3306,
            "dbName": "数据库名称",
            "user": "用户名",
            "password": "密码",
            "other": {
                "sequelize": {
                    "dialect": "mysql",
                    "host": "host地址",
                    "port": 3306,
                    "logging": false,
                    "pool": {
                        "max": 5,
                        "min": 0,
                        "acquire": 30000,
                        "idle": 10000
                    },
                    "timezone": "+08:00",
                    "define": {
                        "freezeTableName": true,
                        "underscored": true,
                        "charset": "utf8",
                        "collate": "utf8_general_ci",
                        "timestamps": false,
                        "paranoid": true
                    }
                }
            }
        }
    }

## 管理后台 (非必须步骤)

前提 : 需要开启数据库配置

修改cfg.json中的manage的room和password，默认房间号和密码都是tlrtcfile

    访问 : http://localhost:9092 或者 http://本机ip:9092

    输入配置的房间号，输入密码，即可进入管理后台

    "manage": {
		"room": "tlrtcfile",
		"password": "tlrtcfile"
	},

## 企微通知 (非必须步骤)

修改cfg.json中的notify的qiwei数组，填入企业微信机器人的key即可

normal : 正常通知, error : 系统报错通知

    "notify": {
        "open": true,  #是否开启企业微信通知
        "qiwei": {
            "normal" : [
                "key1",
                "key2"
            ],
            "error" : [
                "key3",
                "key4"
            ]
        }
    },

## OSS云存储 (非必须步骤)

修改cfg.json中的oss

    "oss": {
		"seafile": {
			"repoid": "",
			"host": "",
			"username": "帐号",
			"password": "密码"
		},
		"alyun": {
			"AccessKey": "",
			"SecretKey": "",
			"bucket": "tl-rtc-file"
		},
		"txyun": {
			"AccessKey": "",
			"SecretKey": "",
			"bucket": "tl-rtc-file"
		},
		"qiniuyun": {
			"AccessKey": "",
			"SecretKey": "",
			"bucket": "tl-rtc-file"
		}
	},

## Chat-GPT (非必须步骤)

修改cfg.json中的openai.apiKeys，填写你自己openai账号生成的apiKey

    "openai": {
		"apiKeys": [
			
		]
	},

## Docker (非必须步骤)

### 使用官方镜像 : 

两种镜像模式选一种即可

http模式镜像:

    docker pull iamtsm/tl-rtc-file-api-local

    docker run --name=api-local -p 9092:9092 -e "WS_HOST=ws://127.0.0.1:8444" -d iamtsm/tl-rtc-file-api-local localapi

    docker pull iamtsm/tl-rtc-file-socket-local

    docker run --name=socket-local -p 8444:8444 -e "WS_HOST=ws://127.0.0.1:8444" -d iamtsm/tl-rtc-file-socket-local localsocket

https模式镜像:

    docker pull iamtsm/tl-rtc-file-api-server

    docker run --name=api-server -p 9092:9092 -e "WSS_HOST=wss://127.0.0.1:8444" -d iamtsm/tl-rtc-file-api-server serverapi

    docker pull iamtsm/tl-rtc-file-socket-server

    docker run --name=socket-server -p 8444:8444 -e "WSS_HOST=wss://127.0.0.1:8444" -d iamtsm/tl-rtc-file-socket-server serversocket


### 自己打包镜像 : 

两种模式选一种操作即可

http模式启动:

    修改 `docker/local.env` 中的配置信息或者按需配置conf.json中的ws, 或者wss (需要填容器的ip，端口信息)
    
    docker-compose --profile=local up -d

    访问 : http://localhost:9092 或者 http://本机ip:9092

https模式启动:

    修改 `docker/local.env` 中的配置信息或者按需配置conf.json中的ws, 或者wss (需要填容器的ip，端口信息)
    
    docker-compose --profile=server up -d

    访问 : https://localhost:9092 或者 https://本机ip:9092


## 其他形式部署 

除了上面的手动安装，docker官方镜像，docker自己打包镜像之外，还支持自动脚本，下载项目后，可以进入bin/目录，选择对应的系统脚本，直接执行即可

如果linux脚本没权限，可以先修改一下脚本的可执行权限 `chmod +x bin/linux/*.sh` 

### linux自动脚本

选一种模式启动即可

- `auto-check-install-local.sh` : 自动检查安装node环境，并自动运行启动http模式服务

- `auto-check-install-server.sh` : 自动检查安装node环境，并自动运行启动https模式服务

### windows自动脚本

选一种模式启动即可

- `auto-check-install-local.bat` : 自动检查安装node环境，并自动运行启动http模式服务

- `auto-check-install-server.bat` : 自动检查安装node环境，并自动运行启动https模式服务


## 概述图

![image](doc/tl-rtc-file-tool.jpg)

## License

### MIT License Copyright (c) 2022 iamtsm

## 免责声明

[免责声明](DISCLAIMER.md)