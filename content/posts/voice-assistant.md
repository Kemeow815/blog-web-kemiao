---
title: voice-assistant
date: 2023-12-13T12:18:40+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1700753227268-8832c285591e?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDI0NDA5Njd8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1700753227268-8832c285591e?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDI0NDA5Njd8&ixlib=rb-4.0.3
---

# [linyiLYi/voice-assistant](https://github.com/linyiLYi/voice-assistant)

# 语音助手

一个简单的 Python 脚本，可以通过语音与本地大语言模型进行对话。

### macOS 安装指南

以下为 macOS 的安装过程，Windows 与 Linux 可以使用 speech_recognition 与 pyttsx3 来替代下文中的 macOS 的 hear 与 say 指令。

#### 创建环境

```
conda create -n VoiceAI python=3.11
conda activate VoiceAI
pip install langchain
CMAKE_ARGS="-DLLAMA_METAL=on" pip install llama-cpp-python

# 安装音频处理工具
brew install portaudio
pip install pyaudio
```

#### 安装 hear 语音识别模块

从开源项目 [hear](https://github.com/sveinbjornt/hear) 中[下载安装包](https://sveinbjorn.org/files/software/hear.zip)，解压文件夹后运行`sudo bash install.sh`（需要管理员权限）。安装完成后可以直接通过控制台指令调用 macOS 的语音识别功能。注意要开启电脑设置里的键盘听写选项：设置 -> 键盘 -> 听写（开启开关）。在 macOS 上首次使用时还要在“设置 -> 隐私与安全性”允许 hear 模块运行。

#### 模型文件
模型文件存放于  `models/` 文件夹下，在脚本中通过变量 `MODEL_PATH` 指定。
推荐下载 TheBloke 与 XeIaso 的 gguf 格式模型，其中 6B 模型显存占用更小：
- [TheBloke/Yi-34B-Chat-GGUF](https://huggingface.co/TheBloke/Yi-34B-Chat-GGUF/blob/main/yi-34b-chat.Q8_0.gguf)
- [XeIaso/Yi-6B-Chat-GGUF](https://huggingface.co/XeIaso/yi-chat-6B-GGUF/blob/main/yi-chat-6b.Q8_0.gguf)
