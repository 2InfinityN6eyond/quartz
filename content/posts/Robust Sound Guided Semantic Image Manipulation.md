---
title: Sound-Guided Semantic Image Manipulation
tags:
  - MACHINE_LEARNING
  - MULTI_MODAL
  - PAPER_REVIEW
---


## Reference

### Sound Guided Image Manipulation
- CLIP과 같은embedding space를 가지는 Audio Encoder를 학습시킨다.
- StyleGAN source latent vector를 조절해 생성된 이미지의 embedding과 sound embedding 사이의 cosine distance가 최소화되도록 한다.
- sound guided semantic manipulation은 잘 되지만, sound input에는 없었던 정보가 들어가는 단점이 있다.
	- 같은 클래스를 가진 여러 오디오가 있는데, contrasive learning을 수행할 때 positive edge가 하나밖에 없다.
	- auido-visual pair에 bias가 있다.
- 


## Robust Sound Guided Semantic Image Manipulation
### audio-visual weakly paired contrasive learning
- 같은 text description을 가졌지만 서로 pair가 아닌 image와 sound 간에 positive weak edge를 형성한다.
- visual-text cosine 유사도 분포와, audio-visual cosine 유사도 분포의 Kullback-Leibler divergence를 최소화한다.
- visual change 는 audio intensity와 비례한다.
- 다른 논문들과의 비교, music style transfer 분야에서의 적용 등을 본다.

### train
- sound representation pre-training step
	- 


## 코드 분석
- youtube_dl 대신 yt_dlp를 써야함.
- vggsound.csv 파일 위치가 바뀌었음.
- StyleGAN pretrain model이 landscape를 생성하는데 argparser의 description에는 어울리지 않는 프롬프트가 있음.
- 또 ir_se_ 를 사용함07 070707070707