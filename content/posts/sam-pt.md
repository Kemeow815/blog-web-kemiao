---
title: sam-pt
date: 2023-07-08T12:19:10+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1685986065382-0a7fe9783797?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODg3ODk3ODB8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1685986065382-0a7fe9783797?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODg3ODk3ODB8&ixlib=rb-4.0.3
---

# [SysCV/sam-pt](https://github.com/SysCV/sam-pt)

# Segment Anything Meets Point Tracking

> [**Segment Anything Meets Point Tracking**](https://arxiv.org/abs/2307.01197) \
> [Frano Rajič](https://m43.github.io/), [Lei Ke](http://www.kelei.site/), [Yu-Wing Tai](https://yuwingtai.github.io/), [Chi-Keung Tang](http://home.cse.ust.hk/~cktang/bio.html), [Martin Danelljan](https://martin-danelljan.github.io/), [Fisher Yu](https://www.yf.io/) \
> ETH Zürich, HKUST, EPFL


![SAM-PT design](assets/figure-1.png?raw=true)

We propose SAM-PT, an extension of the Segment Anything Model (SAM) for zero-shot video segmentation. Our work offers a simple yet effective point-based perspective in video object segmentation research. For more details, refer to our paper. Our code, models, and evaluation tools will be released soon. Stay tuned!

## Interactive Video Segmentation Demo
Annotators only provide a few points to denote the target object at the first video frame to get video segmentation results. Please visit our [project page](https://www.vis.xyz/pub/sam-pt/) for more visualizations, including qualitative results on DAVIS 2017 videos and more Avatar clips.
<p float="left">
  <img alt="street" src="assets/street.gif?raw=true" width="48%" /> 
  <img alt="bees" src="assets/bees.gif?raw=true" width="48%" /> 
  <img alt="avatar" src="assets/avatar.gif?raw=true" width="48%" />
  <img alt="horsejump-high" src="assets/horsejump-high.gif?raw=true" width="48%" />
</p>

## Semi-supervised Video Object Segmentation (VOS)
SAM-PT is the first method to utilize sparse point tracking combined with SAM for video segmentation. With such compact mask representation, we achieve the highest $\mathcal{J\\&F}$ scores on the DAVIS 2016 and 2017 validation subsets among methods that do not utilize any video segmentation data during training.
![table-1](assets/table-1.png?raw=true)

Quantitative results in semi-supervised VOS on the validation subsets of DAVIS 2017, YouTube-VOS 2018, and MOSE 2023:
![table-3](assets/table-3.png?raw=true)
![table-4](assets/table-4.png?raw=true)
![table-5](assets/table-5.png?raw=true)

## Video Instance Segmentation (VIS)

On the validation split of UVO VideoDenseSet v1.0, SAM-PT outperforms TAM even though the former was not trained on any video segmentation data. TAM is a concurrent approach combining SAM and XMem, where XMem was pre-trained on BL30K and trained on DAVIS and YouTube-VOS, but not on UVO. On the other hand, SAM-PT combines SAM with the PIPS point tracking method, both of which have not been trained on any video segmentation tasks.
![table-6](assets/table-6.png?raw=true)

## Acknowledgments

We want to thank [SAM](https://github.com/facebookresearch/segment-anything), [PIPS](https://github.com/aharley/pips), [HQ-SAM](https://github.com/SysCV/sam-hq), and [XMem](https://github.com/hkchengrex/XMem) for publicly releasing their code and pretrained models.

## Citation

If you find SAM-PT useful in your research or if you refer to the results mentioned in this repository, please star :star: this repository and consider citing :pencil::
```bibtex
@article{sam-pt,
  title   = {Segment Anything Meets Point Tracking},
  author  = {Rajič, Frano and Ke, Lei and Tai, Yu-Wing and Tang, Chi-Keung and Danelljan, Martin and Yu, Fisher},
  journal = {arXiv:2307.01197},
  year    = {2023}
}
```
