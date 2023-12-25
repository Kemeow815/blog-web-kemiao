---
title: AnimateAnyone-unofficial
date: 2023-12-25T12:17:34+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1702241234961-b3f7861f57d7?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDM0Nzc3NDh8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1702241234961-b3f7861f57d7?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDM0Nzc3NDh8&ixlib=rb-4.0.3
---

# [guoqincode/AnimateAnyone-unofficial](https://github.com/guoqincode/AnimateAnyone-unofficial)

# Unofficial Implementation of Animate Anyone

If you find this repository helpful, please consider giving us a star⭐!

## Overview
This repository contains an simple and unofficial implementation of [Animate Anyone](https://humanaigc.github.io/animate-anyone/). This project is built upon [magic-animate](https://github.com/magic-research/magic-animate/tree/main) and [AnimateDiff](https://github.com/guoyww/AnimateDiff).

## News 🤗🤗🤗
The first training phase basic test passed, currently in training and testing the second phase.

~~Training may be slow due to GPU shortage.😢~~

It only takes a few days to release the weights.😄

## Sample of Stage 1 Result on UBC-fashion dataset
Special thanks to [Zhenzhi Wang](https://zhenzhiwang.github.io/) for assistance with code development and training.
The current version of the face also has some artifacts.  Also, this is a model trained on a UBC dataset rather than a large-scale dataset.

<table class="center">
    <tr><td><img src="./assets/stage1/1.png"></td><td><img src="./assets/stage1/2.png"></td></tr>
    <tr><td><img src="./assets/stage1/3.png"></td><td><img src="./assets/stage1/8.png"></td></tr>
    <tr><td><img src="./assets/stage1/9.png"></td><td><img src="./assets/stage1/10.png"></td></tr>
    <tr><td><img src="./assets/stage1/4.png"></td><td><img src="./assets/stage1/5.png"></td></tr>
    <tr><td><img src="./assets/stage1/6.png"></td><td><img src="./assets/stage1/7.png"></td></tr>

</table>
<p style="margin-left: 2em; margin-top: -1em"></p>

## Note !!!
This project is under continuous development in part-time, there may be bugs in the code, welcome to correct them, I will optimize the code after the pre-trained model is released!

In the current version, we recommend training on 8 or 16 A100,H100 (80G) at 512 or 768 resolution. **Low resolution (256,384) does not give good results!!!(VAE is very poor at reconstruction at low resolution.)**

## ToDo
- [x] **Release Training Code.**
- [x] **Release Inference Code.** 
- [ ] **Release Unofficial Pre-trained Weights. <font color="red">(Note:Train on public datasets instead of large-scale private datasets, just for academic research.🤗)</font>**
- [ ] **Release Gradio Demo.**

## Requirements

```bash
bash fast_env.sh
```

## 🎬Gradio Demo (will publish with weights.)
```python
python3 -m demo.gradio_animate
```

If you only have a GPU with 24 GB of VRAM, I recommend inference at resolution 512 and below.


## Training

#### First Stage

```python
torchrun --nnodes=8 --nproc_per_node=8 train.py --config configs/training/train_stage_1.yaml
```

#### Second Stage

```python
torchrun --nnodes=8 --nproc_per_node=8 train.py --config configs/training/train_stage_2.yaml
```


## Acknowledgements
Special thanks to the original authors of the [Animate Anyone](https://humanaigc.github.io/animate-anyone/) project and the contributors to the [magic-animate](https://github.com/magic-research/magic-animate/tree/main) and [AnimateDiff](https://github.com/guoyww/AnimateDiff) repository for their open research and foundational work that inspired this unofficial implementation.

## Email
guoqin@stu.pku.edu.cn

My response may be slow, please don't ask me nonsense questions.
