---
title: consistencydecoder
date: 2023-11-09T12:17:56+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1694813646419-01c9ca785c57?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTk1MDMzMDZ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1694813646419-01c9ca785c57?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTk1MDMzMDZ8&ixlib=rb-4.0.3
---

# [openai/consistencydecoder](https://github.com/openai/consistencydecoder)

# Consistency Decoder

[[DALL·E 3]](https://openai.com/dall-e-3)
[[Improving Image Generation with Better Captions]](https://cdn.openai.com/papers/dall-e-3.pdf)
[[Consistency Models]](https://arxiv.org/abs/2303.01469)

Improved decoding for stable diffusion vaes.

## Installation

```
$ pip install git+https://github.com/openai/consistencydecoder.git
```

## Usage

```python
import torch
from diffusers import StableDiffusionPipeline
from consistencydecoder import ConsistencyDecoder, save_image, load_image

# encode with stable diffusion vae
pipe = StableDiffusionPipeline.from_pretrained(
    "runwayml/stable-diffusion-v1-5", torch_dtype=torch.float16, device="cuda:0"
)
pipe.vae.cuda()
decoder_consistency = ConsistencyDecoder(device="cuda:0") # Model size: 2.49 GB

image = load_image("assets/gt1.png", size=(256, 256), center_crop=True)
latent = pipe.vae.encode(image.half().cuda()).latent_dist.mean

# decode with gan
sample_gan = pipe.vae.decode(latent).sample.detach()
save_image(sample_gan, "gan.png")

# decode with vae
sample_consistency = decoder_consistency(latent)
save_image(sample_consistency, "con.png")
```

## Examples
 Original Image | GAN Decoder | Consistency Decoder |
:---:|:---:|:---:|
![Original Image](assets/gt1.png) | ![GAN Image](assets/gan1.png) | ![VAE Image](assets/con1.png) |
![Original Image](assets/gt2.png) | ![GAN Image](assets/gan2.png) | ![VAE Image](assets/con2.png) |
![Original Image](assets/gt3.png) | ![GAN Image](assets/gan3.png) | ![VAE Image](assets/con3.png) |
