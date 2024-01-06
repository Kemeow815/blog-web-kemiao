---
title: Open-AnimateAnyone
date: 2024-01-06T12:17:20+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1703426108384-f5f3f45de1aa?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDQ1MTQ1MTl8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1703426108384-f5f3f45de1aa?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDQ1MTQ1MTl8&ixlib=rb-4.0.3
---

# [guoqincode/Open-AnimateAnyone](https://github.com/guoqincode/Open-AnimateAnyone)

# Unofficial Implementation of Animate Anyone

If you find this repository helpful, please consider giving us a star⭐!

We only train on small-scale datasets (such as TikTok, UBC), and it is difficult to achieve official results under the condition of insufficient data scale and quality. Because of the consideration of time and cost, we do not intend to collect and filter a large number of high-quality data. If someone has a robust model trained on a large amount of high-quality data and is willing to share it, make a pull request.

## Overview
This repository contains an simple and unofficial implementation of [Animate Anyone](https://humanaigc.github.io/animate-anyone/). This project is built upon [magic-animate](https://github.com/magic-research/magic-animate/tree/main) and [AnimateDiff](https://github.com/guoyww/AnimateDiff). This implementation is first developed by [Qin Guo](https://github.com/guoqincode) and then assisted by [Zhenzhi Wang](https://zhenzhiwang.github.io/).

## News 🤗🤗🤗
The first training phase basic test passed, currently in training and testing the second phase.

~~Training may be slow due to GPU shortage.😢~~

It only takes a few days to release the weights.😄

## Sample of Result on UBC-fashion dataset
### Stage 1
The current version of the face still has some artifacts.  This model is trained on the UBC dataset rather than a large-scale dataset.
<table class="center">
    <tr><td><img src="./assets/stage1/1.png"></td><td><img src="./assets/stage1/2.png"></td></tr>
    <tr><td><img src="./assets/stage1/3.png"></td><td><img src="./assets/stage1/8.png"></td></tr>
    <tr><td><img src="./assets/stage1/9.png"></td><td><img src="./assets/stage1/10.png"></td></tr>
    <tr><td><img src="./assets/stage1/4.png"></td><td><img src="./assets/stage1/5.png"></td></tr>
    <tr><td><img src="./assets/stage1/6.png"></td><td><img src="./assets/stage1/7.png"></td></tr>

</table>
<p style="margin-left: 2em; margin-top: -1em"></p>

### Stage 2
The training of stage2 is challenging due to artifacts in the background. We select one of our best results here, and are still working on it. An important point is to ensure that training and inference resolution is consistent.
<table class="center">
    <tr><td><img src="./assets/stage2/1.gif"></td></tr>

</table>
<p style="margin-left: 2em; margin-top: -1em"></p>


## Note !!!
This project is under continuous development in part-time, there may be bugs in the code, welcome to correct them, I will optimize the code after the pre-trained model is released!

In the current version, we recommend training on 8 or 16 A100,H100 (80G) at 512 or 768 resolution. **Low resolution (256,384) does not give good results!!!(VAE is very poor at reconstruction at low resolution.)**

## ToDo
- [x] **Release Training Code.**
- [x] **Release Inference Code.** 
- [ ] **Release Unofficial Pre-trained Weights.**
- [x] **Release Gradio Demo.**

## Requirements

```bash
bash fast_env.sh
```

## 🎬Gradio Demo
```python
python3 -m demo.gradio_animate
```
For a 13-second pose video, processing at 256 resolution requires 11G VRAM, and at 512 resolution, it requires 23.5G VRAM.

## Training
### Original AnimateAnyone Architecture (It is difficult to control pose when training on a small dataset.)
#### First Stage

```python
torchrun --nnodes=8 --nproc_per_node=8 train.py --config configs/training/train_stage_1.yaml
```

#### Second Stage

```python
torchrun --nnodes=8 --nproc_per_node=8 train.py --config configs/training/train_stage_2.yaml
```

### Our Method (A more dense pose control scheme, the number of parameters is still small.) (Highly recommended)
```python
torchrun --nnodes=8 --nproc_per_node=8 train_hack.py --config configs/training/train_stage_1.yaml
```

#### Second Stage

```python
torchrun --nnodes=8 --nproc_per_node=8 train_hack.py --config configs/training/train_stage_2.yaml
```


## Acknowledgements
Special thanks to the original authors of the [Animate Anyone](https://humanaigc.github.io/animate-anyone/) project and the contributors to the [magic-animate](https://github.com/magic-research/magic-animate/tree/main) and [AnimateDiff](https://github.com/guoyww/AnimateDiff) repository for their open research and foundational work that inspired this unofficial implementation.
