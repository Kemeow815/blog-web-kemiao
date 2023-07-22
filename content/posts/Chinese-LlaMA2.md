---
title: Chinese-LlaMA2
date: 2023-07-22T12:16:34+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1687278835925-0f5d6baf8925?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODk5OTkyNTZ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1687278835925-0f5d6baf8925?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODk5OTkyNTZ8&ixlib=rb-4.0.3
---

# [michael-wzhu/Chinese-LlaMA2](https://github.com/michael-wzhu/Chinese-LlaMA2)

# Chinese-LlaMA2

<p align="center">
    <br>
    <img src="./assets/chinese-llama2-banner.png" width="600"/>
    <br>
</p>
<p align="center">
    <img alt="GitHub" src="https://img.shields.io/github/license/ymcui/Chinese-LLaMA-Alpaca.svg?color=blue&style=flat-square">
    <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/ymcui/Chinese-LLaMA-Alpaca">
</p>

就在不久前，Meta最新开源了Llama 2模型，完全可商用，看来Meta势必要与OpenAI (ClosedAI) 硬刚到底。虽然Llama 2对原版的LlaMA模型做了升级，但是其仍然对中文没有太好的支持，需要在中文上做定制化。所以我们决定在次开展Llama 2的中文汉化工作：
- ⏳[Chinese-LlaMA2](https://huggingface.co/michaelwzhu/Chinese-LlaMA2-7B): 对Llama 2进行中文预训练；
  - 第一步：先在42G中文预料上进行训练；后续将会加大训练规模 
- ⏳[Chinese-LlaMA2-chat](https://huggingface.co/michaelwzhu/Chinese-LlaMA2-7B-chat): 对[Chinese-LlaMA2](https://huggingface.co/michaelwzhu/Chinese-LlaMA2-7B)进行指令微调和多轮对话微调，以适应各种应用场景和多轮对话交互。

同时我们也考虑更为快速的中文适配方案：
- ⏳Chinese-LlaMA2-sft-v0: 采用现有的开源中文指令微调或者是对话数据，对LlaMA-2进行直接微调 (将于近期开源)

注意，为了遵循相应的许可，我们将不会发布完整的模型权重，只发布LoRA权重，其与Meta的LlaMA2权重合并即可形成Chinese-LlaMA2模型。

同时，我们将会围绕Chinese-LlaMA2打造各种垂直领域模型：
- ⏳[Chinese-LlaMA2-chatmed](https://huggingface.co/michaelwzhu/Chinese-LlaMA2-7B-chatmed): Chinese-LlaMA2医学领域大模型，支持多轮在线问诊；
- ⏳[Chinese-LlaMA2-tcm](https://huggingface.co/michaelwzhu/Chinese-LlaMA2-7B-tcm): Chinese-LlaMA2中医药大模型，专注于中医药细分领域，赋能中医药传承


## 更新

2023/07/19 启动LlaMA-2中文大模型；



## 操作步骤

### 获得llama-2权重

现在LlaMA-2权重需要在Meta指定的官方网站申请，具体说明见[LlaMA-的hf页面](https://huggingface.co/meta-llama/Llama-2-70b-hf)。当你没有通过申请时，在这个网页上看到的是一个申请表，你需要根据他的说明进行申请，申请通过后就可以看到权重文件了。

### 扩充词表和扩展embedding层

我们现在采用的方案是：使用[Chinese-LLaMA](https://github.com/ymcui/Chinese-LLaMA-Alpaca)的词表，该词表是对llama原始词表的扩充，将词汇量从32000扩展到49953大小。同时LlaMA-2模型会进行embedding层的resize，即采用随机初始化的参数扩展embedding层和lm_head层。

在一些我们关注的垂直领域，我们后续也会自己训一个sentencepiece模型来更新llama-2的词表。

### 继续预训练

由于扩展词表后，LlaMA-2的embedding层和lm_head层会有随机初始化的参数，所以我们需要采用大规模的预训练学习中文语料的知识。预训练运行以下命令(数据，模型的路径，卡数等需要自行配置)：

```bash
CUDA_VISIBLE_DEVICES="2,3" ./src/further_ft/run_train.sh

```



## 评测交流与技术交流

PromptCBLUE与大模型技术交流微信交流群二维码（截止至7月23日有效）：
<p align="left">
    <br>
    <img src="./assets/wechat_qrcode.jpg" width="300"/>
    <br>
</p>


## 团队介绍

本项目由华东师范大学计算机科学与技术学院智能知识管理与服务团队完成，团队指导老师为王晓玲教授。