---
title: dreamtalk
date: 2024-01-05T12:17:42+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1631559416257-aca23abbe832?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDQ0MjgxNjZ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1631559416257-aca23abbe832?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDQ0MjgxNjZ8&ixlib=rb-4.0.3
---

# [ali-vilab/dreamtalk](https://github.com/ali-vilab/dreamtalk)

<h2 align="center">DreamTalk: When Expressive Talking Head Generation <br> Meets Diffusion Probabilistic Models</h2>
<p align="center">
  <a href='https://dreamtalk-project.github.io/'><img src='https://img.shields.io/badge/Project-Page-Green'></a> <a href='https://arxiv.org/abs/2312.09767'><img src='https://img.shields.io/badge/Paper-Arxiv-red'></a> <a href='https://youtu.be/VF4vlE6ZqWQ'><img src='https://badges.aleen42.com/src/youtube.svg'></a>
</p>

![teaser](media/teaser.gif "teaser")

DreamTalk is a diffusion-based audio-driven expressive talking head generation framework that can produce high-quality talking head videos across diverse speaking styles. DreamTalk exhibits robust performance with a diverse array of inputs, including songs, speech in multiple languages, noisy audio, and out-of-domain portraits.

## News
- __[2023.12]__ Release inference code and pretrained checkpoint.

## Installation

```
conda create -n dreamtalk python=3.7.0
conda activate dreamtalk
pip install -r requirements.txt
conda install pytorch==1.8.0 torchvision==0.9.0 torchaudio==0.8.0 cudatoolkit=11.1 -c pytorch -c conda-forge
conda update ffmpeg

pip install urllib3==1.26.6
pip install transformers==4.28.1
pip install dlib
```

## Download Checkpoints
Download the checkpoint of the denoising network and the renderer:
* [HuggingFace](https://huggingface.co/damo-vilab/dreamtalk)
* [ModelScope](https://modelscope.cn/models/damo/dreamtalk/files) (in `checkpoints` folder)


Put the downloaded checkpoints into `checkpoints` folder.


## Inference
Run the script:

```
python inference_for_demo_video.py \
--wav_path data/audio/acknowledgement_english.m4a \
--style_clip_path data/style_clip/3DMM/M030_front_neutral_level1_001.mat \
--pose_path data/pose/RichardShelby_front_neutral_level1_001.mat \
--image_path data/src_img/uncropped/male_face.png \
--cfg_scale 1.0 \
--max_gen_len 30 \
--output_name acknowledgement_english@M030_front_neutral_level1_001@male_face
```

`wav_path` specifies the input audio. The input audio file extensions such as wav, mp3, m4a, and mp4 (video with sound) should all be compatible.

`style_clip_path` specifies the reference speaking style and `pose_path` specifies head pose. They are 3DMM paramenter sequences extracted from reference videos. You can follow [PIRenderer](https://github.com/RenYurui/PIRender) to extract 3DMM parameters from your own videos. Note that the video frame rate should be 25 FPS. Besides, videos used for head pose reference should be first cropped to $256\times256$ using scripts in [FOMM video preprocessing](https://github.com/AliaksandrSiarohin/video-preprocessing).

`image_path` specifies the input portrait. Its resolution should be larger than $256\times256$. Frontal portraits, with the face directly facing forward and not tilted to one side, usually achieve satisfactory results. The input portrait will be cropped to $256\times256$. If your portrait is already cropped to $256\times256$ and you want to disable cropping, use option `--disable_img_crop` like this:

```
python inference_for_demo_video.py \
--wav_path data/audio/acknowledgement_chinese.m4a \
--style_clip_path data/style_clip/3DMM/M030_front_surprised_level3_001.mat \
--pose_path data/pose/RichardShelby_front_neutral_level1_001.mat \
--image_path data/src_img/cropped/zp1.png \
--disable_img_crop \
--cfg_scale 1.0 \
--max_gen_len 30 \
--output_name acknowledgement_chinese@M030_front_surprised_level3_001@zp1
```

`cfg_scale` controls the scale of classifer-free guidance. It can adjust the intensity of speaking styles.

`max_gen_len` is the maximum video generation duration, measured in seconds. If the input audio exceeds this length, it will be truncated.

The generated video will be named `$(output_name).mp4` and put in the output_video folder. Intermediate results, including the cropped portrait, will be in the `tmp/$(output_name)` folder.

Sample inputs are presented in `data` folder. Due to copyright issues, we are unable to include the songs we have used in this folder.


## Acknowledgements

We extend our heartfelt thanks for the invaluable contributions made by preceding works to the development of DreamTalk. This includes, but is not limited to:
[PIRenderer](https://github.com/RenYurui/PIRender)
,[AVCT](https://github.com/FuxiVirtualHuman/AAAI22-one-shot-talking-face)
,[StyleTalk](https://github.com/FuxiVirtualHuman/styletalk)
,[Deep3DFaceRecon_pytorch](https://github.com/sicxu/Deep3DFaceRecon_pytorch)
,[Wav2vec2.0](https://huggingface.co/jonatasgrosman/wav2vec2-large-xlsr-53-english)
,[diffusion-point-cloud](https://github.com/luost26/diffusion-point-cloud)
,[FOMM video preprocessing](https://github.com/AliaksandrSiarohin/video-preprocessing). We are dedicated to advancing upon these foundational works with the utmost respect for their original contributions.

## Citation
If you find this codebase useful for your research, please use the following entry.
```BibTeX
@article{ma2023dreamtalk,
  title={DreamTalk: When Expressive Talking Head Generation Meets Diffusion Probabilistic Models},
  author={Ma, Yifeng and Zhang, Shiwei and Wang, Jiayu and Wang, Xiang and Zhang, Yingya and Deng, Zhidong},
  journal={arXiv preprint arXiv:2312.09767},
  year={2023}
}
```


