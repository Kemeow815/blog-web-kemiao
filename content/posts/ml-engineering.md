---
title: ml-engineering
date: 2023-10-14T12:16:18+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1695742865516-2d6b264414eb?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTcyNTY4ODJ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1695742865516-2d6b264414eb?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTcyNTY4ODJ8&ixlib=rb-4.0.3
---

# [stas00/ml-engineering](https://github.com/stas00/ml-engineering)

# Machine Learning Engineering Guides and Tools

An open collection of methodologies to help with successful training of large language models and multi-modal models.

This is a technical material suitable for LLM/VLM training engineers and operators. That is the content here contains lots of scripts and copy-n-paste commands to enable you to quickly address your needs.

This repo is an ongoing brain dump of my experiences training Large Language Models (LLM) (and VLMs); a lot of the know-how I acquired while training the open-source [BLOOM-176B](https://huggingface.co/bigscience/bloom) model in 2022 and
[IDEFICS-80B](https://huggingface.co/HuggingFaceM4/idefics-80b-instruct) multi-modal model in 2023. Currently, I'm working on developing/training open-source Retrieval Augmented models at [Contextual.AI](https://contextual.ai/).

I've been compiling this information mostly for myself so that I could quickly find solutions I have already researched in the past and which have worked, but as usual I'm happy to share these with the wider ML community.


## [Debugging software and hardware failures](./debug/)

## [Fault Tolerance](./fault-tolerance/)

## [Performance](./performance/)

## [Multi-Node networking](./multi-node)

## [Model parallelism](./model-parallelism/)

## [Tensor precision / Data types](./dtype/)

## [Training hyper-parameters and model initializations](./hparams/)

## [Reproducibility](./reproducibility/)

## [Instabilities](./instabilities/)

## [SLURM](./slurm/)

## [Resources](./resources/)

## [HF Transformers notes](./transformers/)


## Gratitude

None of this would have been possible without me being entrusted with doing the specific LLM/VLM trainings I have learned this know-how from. This is a privilege that only a few enjoy due to the prohibitively expensive cost of renting huge ML compute clusters. So hopefully the rest of the ML community will vicariously learn from these notes.

Special thanks go to [Thom Wolf](https://github.com/thomwolf) who proposed that I lead the BLOOM-176B training when I didn't know anything about large scale training. This was the project that catapulted me into the intense learning process. And, of course, HuggingFace for giving me the opportunity to work full time on BLOOM-176B and later on IDEFICS-80B trainings.

## Contributing

If you found a bug, typo or would like to propose an improvement please don't hesitate to open an [Issue](https://github.com/stas00/ml-engineering/issues) or contribute a PR.


## License

The content of this site is distributed under [Attribution-ShareAlike 4.0 International](./LICENSE-CC-BY-SA).
