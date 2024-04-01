---
title: AIOS
date: 2024-04-01T12:16:05+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1710225342718-11c18a806f59?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTE5NDQ5NDN8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1710225342718-11c18a806f59?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTE5NDQ5NDN8&ixlib=rb-4.0.3
---

# [agiresearch/AIOS](https://github.com/agiresearch/AIOS)

# AIOS: LLM Agent Operating System

<a href='https://arxiv.org/abs/2403.16971'><img src='https://img.shields.io/badge/Paper-PDF-red'></a> 
<a href='https://arxiv.org/abs/2312.03815'><img src='https://img.shields.io/badge/Paper-PDF-blue'></a> 
[![Code License](https://img.shields.io/badge/Code%20License-MIT-green.svg)](https://github.com/agiresearch/AIOS/blob/main/LICENSE)

AIOS, a Large Language Model (LLM) Agent operating system, embeds large language model into Operating Systems (OS) as the brain of the OS, enabling an operating system "with soul" -- an important step towards AGI. AIOS is designed to optimize resource allocation, facilitate context switch across agents, enable concurrent execution of agents, provide tool service for agents, maintain access control for agents, and provide a rich set of toolkits for LLM Agent developers.


## 🏠 Architecture of AIOS
<p align="center">
<img src="images/AIOS-Architecture.png">
</p>


## 📰 News
- **[2024-03-25]** ✈️ Our paper [AIOS: LLM Agent Operating System](https://arxiv.org/abs/2403.16971) is released and AIOS repository is officially launched!
- **[2023-12-06]** 📋 After several months of working, our perspective paper [LLM as OS, Agents as Apps: Envisioning AIOS, Agents and the AIOS-Agent Ecosystem](https://arxiv.org/abs/2312.03815) is officially released.

## ✈️ Getting Started

### Installation
```bash
git clone https://github.com/agiresearch/AIOS.git
```
**Make sure you have Python >= 3.9**  
Install the required packages using pip  
```bash
pip install -r requirements.txt
```

### Usage

### Run with locally-deployed LLM
Set up [Hugging Face token](https://huggingface.co/settings/tokens) and cache directory
```bash
export HUGGING_FACE_HUB_TOKEN=<YOUR READ TOKEN>
export HF_HOME=<YOUR CACHE DIRECTORY>
```
Replace the max_gpu_memory and eval_device with your own and run

```python
# Use Gemma-2b-it
python main.py --llm_name gemma-2b-it --max_gpu_memory '{"0": "24GB"}' --eval_device "cuda:0" --max_new_tokens 256
```

```python
# Use Mixtral-8x7b-it
python main.py --llm_name mixtral-8x7b-it --max_gpu_memory '{"0": "48GB", "1": "48GB", "2": "48GB"}' --eval_device "cuda:0" --max_new_tokens 256
```
### Run with LLM API
Run with Gemini-pro, setup [Gemini API Key](https://aistudio.google.com/app/apikey)
```bash
export GEMINI_API_KEY=<YOUR GEMINI API KEY>
```
```python
# Use Gemini-pro
python main.py --llm_name gemini-pro
```

## 🌟 Join Us!
AIOS is dedicated to facilitating LLM agents' development and deployment in a systematic way, we are always looking for passionate collaborators to join us to foster a more cohesive, effective and efficient AIOS-Agent ecosystem. Suggestions and pull requests are always welcome!

## 🖋️ Citation
```
@article{mei2024aios,
  title={AIOS: LLM Agent Operating System},
  author={Mei, Kai and Li, Zelong and Xu, Shuyuan and Ye, Ruosong and Ge, Yingqiang and Zhang, Yongfeng}
  journal={arXiv:2403.16971},
  year={2024}
}
@article{ge2023llm,
  title={LLM as OS, Agents as Apps: Envisioning AIOS, Agents and the AIOS-Agent Ecosystem},
  author={Ge, Yingqiang and Ren, Yujie and Hua, Wenyue and Xu, Shuyuan and Tan, Juntao and Zhang, Yongfeng},
  journal={arXiv:2312.03815},
  year={2023}
}
```

## 📪 Contact
If you have any suggestions, or wish to contact us for any reason, feel free to email us at marknju2018@gmail.com
