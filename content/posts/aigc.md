---
title: aigc
date: 2023-07-03T12:19:46+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1685725083464-26cab8f2da1e?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODgzNTc4MjZ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1685725083464-26cab8f2da1e?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODgzNTc4MjZ8&ixlib=rb-4.0.3
---

# [phodal/aigc](https://github.com/phodal/aigc)

# 构筑大语言模型应用：应用开发与架构设计

> aka. Unlocking the Potential of Large Language Models: Real-World Use Cases

2023 年的上半年里，我（@phodal）和 Thoughtworks
的同事们（如：@[tianweiliu](https://github.com/tianweiliu)、@[teobler](https://github.com/teobler)、@[mutoe](https://github.com/mutoe)
等）、
开源社区的同伴们（如：
卷王@[CGQAQ](https://github.com/CGQAQ)、@[genffy](https://github.com/genffy)、 @[liruifengv](https://github.com/liruifengv)
等)
一起，创建了一系列的流行的或者不流行的开源项目。它们涉及了：

- LLM 能力的充分运用
  - Prompt 编写：Prompt 学习与编写模式
  - Prompt 管理：Prompt 即代码
- LLM 下的软件开发工序及应用架构设计
  - 新的交互设计：Chat 模式
  - 大模型友好的工序：基于 AI 2.0 （ChatGPT + Copilot）如何去设计软件开发流程
  - LLM 应用架构的设计与落地：Unit Mesh
- 面向特定场景的 LLM 应用
  - 基于开源模型构建自己的模型：特定场景的模型微调 + LLMOps
  - 上下文工程（prompt 工程）：LLM 应用的核心

围绕于上述的一系列内容，我们也在思考软件开发能给我们带来了什么。所以，我重新整理了过去半年的一些思考、文章，重新编写了这本开源电子书，希望能够帮助到大家。

关注我的微信公众号（搜索 phodal-weixin），获得更多及时的更新：

![微信公众号](src/images/qrcode.jpg)

我们发起的相关开源项目如下（包括但是不限于）：

| 名称                                                                       | 描述                                                                                                                                                | 类型                   | Stars                                                                                          |
| -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | ---------------------------------------------------------------------------------------------- |
| [理解 Prompt](https://github.com/prompt-engineering/understand-prompt)     | 基于编程、绘画、写作的 AI 探索与总结。                                                                                                              | 文档                   | ![GitHub Repo stars](https://img.shields.io/github/stars/prompt-engineering/understand-prompt) |
| [Prompt 编写模式](https://github.com/prompt-engineering/prompt-patterns)   | 如何将思维框架赋予机器，以设计模式的形式来思考 prompt。                                                                                             | 文档                   | ![GitHub Repo stars](https://img.shields.io/github/stars/prompt-engineering/prompt-patterns)   |
| [ClickPrompt](https://github.com/prompt-engineering/click-prompt)          | 用于一键轻松查看、分享和执行您的 Prompt。                                                                                                           | 应用                   | ![GitHub Repo stars](https://img.shields.io/github/stars/prompt-engineering/click-prompt)      |
| [ChatVisualNovel](https://github.com/prompt-engineering/chat-visual-novel) | 基于 ChatGPT 的定制化视觉小说引擎                                                                                                                   | 应用                   | ![GitHub Repo stars](https://img.shields.io/github/stars/prompt-engineering/chat-visual-novel) |
| [ChatFlow](https://github.com/prompt-engineering/chat-flow)                | 打造个性化 ChatGPT 流程，构建自动化之路。                                                                                                           | 框架                   | ![GitHub Repo stars](https://img.shields.io/github/stars/prompt-engineering/chat-flow)         |
| [Unit Mesh](https://github.com/unit-mesh/unit-mesh)                        | 基于 AI 为核心的软件 2.0 思想的软件架构。                                                                                                           | 架构                   | ![GitHub Repo stars](https://img.shields.io/github/stars/unit-mesh/unit-mesh)                  |
| [Unit Minions](https://github.com/unit-mesh/unit-minions)                  | AI 研发提效研究：自己动手训练 LoRA                                                                                                                  | 微调教程、指南、数据集 | ![GitHub Repo stars](https://img.shields.io/github/stars/unit-mesh/unit-minions)               |
| [Unit Runtime](https://github.com/unit-mesh/unit-runtime)                  | 一个 ChatGPT 等 AI 代码的运行环境，可一键启动并实时交互，帮助您快速构建和测试 AI 代码。                                                             | 基础设施               | ![GitHub Repo stars](https://img.shields.io/github/stars/unit-mesh/unit-runtime)               |
| [DevTi](https://github.com/unit-mesh/devti)                                | 基于 LLM 的微调来提供全面智能化解决方案，助力开发人员高效完成开发任务，以实现自动化用户任务拆解、用户故事生成、自动化代码生成、自动化测试生成等等。 | 微调代码               | ![GitHub Repo stars](https://img.shields.io/github/stars/unit-mesh/devti)                      |
| [AutoDev](https://github.com/unit-mesh/auto-dev)                           | 一款 Intellij IDEA 的 LLM/AI 辅助编程插件。AutoDev 能够与您的需求管理系统（例如 Jira、Trello、Github Issue 等）直接对接。                           | IDEA 插件              | ![GitHub Repo stars](https://img.shields.io/github/stars/unit-mesh/auto-dev)                   |
| [ArchGuard Co-mate](https://github.com/archguard/co-mate)                  | 基于人工智能技术的架构副驾驶、设计和治理工具                                                                                                        | 架构协同应用           | ![GitHub Repo stars](https://img.shields.io/github/stars/archguard/co-mate)                    |

我们在 QCon
上的演讲：[演讲：探索软件开发新工序：LLM 赋能研发效能提升](https://qcon.infoq.cn/2023/guangzhou/presentation/5319)

> LLM（如 ChatGPT + GitHub
> Copilot）作为一种创新的工具组合，为我们带来了全新的机遇。它能够帮助业务人员和开发者在需求、架构、编码、测试等环节提高效率和质量，实现从设计到验证的端到端流程。在本次分享中，我将向大家介绍
> LLM 在研发效能方面的应用场景和实践案例，展示它是如何在各个环节中发挥作用的。同时，我们还将分享如何构建私有化的 LLM
> 工程化方式，使其更好地适应组织的需求。欢迎对 LLM + 研发效能感兴趣的朋友们参加本次分享，与我们一起探讨研发效能的未来。

我们在 Bilibili 上的大语言模型微调相关的视频：

- LLaMA
  系列在线视频： 《[代码辅助生成](https://www.bilibili.com/video/BV1Rh411u74H/)》 、《[测试代码生成](https://www.bilibili.com/video/BV1jg4y1G7Xc/)》 、《[详细需求生成](https://www.bilibili.com/video/BV1Us4y1N7rd/)》 、《[文本转 SQL](https://www.bilibili.com/video/BV1uv4y1H7bg/)》
- ChatGLM 系列在线视频： 《[LoRA 大比拼：ChatGLM vs LLaMA，谁更会写需求文档？](https://www.bilibili.com/video/BV1fv4y1n7Y3/)》

欢迎大家一起来参与我们的开源项目，一起来探索 LLM + 软件开发的未来。
