---
title: "Converting StyleGAN2 tensorflow1 model to pytorch"
tags:
- "MACHINE LEARNING"
- "SKILL"
- "PROGRAMMING"
---

- 세팅
	- 필요한 가상환경들이 이미 설정되어  있다고 가정 
		- 가상환경 요구사항 
			- StyleGAN2-ada tensorflow1 구현 버전 
				- 코드를 작동시키려면 tensorflow 1.14.0 -or 1.15.0 버전이 필요함.
				- tensorflow 1.15.0 은 python 3.6 or 3.7 이랑 cuda toolkit 10.0을 요구함.
				- model weight 변환 과정에서 cuda 의존성을 맞출 필요는 없음.
			- StyleGAN2-ada pytorch 구현 버전
				- 그리 까다롭지 않은듯
``` zsh

$TF_ENV="<python3.7버전, tensorflow 1.15.0이 설치된 가상환경 이름>"
$TORCH_ENV="<pytorch가 준비된 가상환경>"

$PROJECT_ROOT="TF2TORCH"
mkdir $PROJECT_ROOT && cd $PROJECT_ROOT
```

- [SytleGAN2-ada tf 버전 리포](https://github.com/NVlabs/stylegan2-ada.git) 세팅.
- 여러 pretrained 모델 중 ffhq.pkl 을 받을거임 ([전체 pretrained weights 리스트](https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada/pretrained/))
``` zsh
git clone https://github.com/NVlabs/stylegan2-ada.git

cd stylegan2-ada
mkdir pretrained && cd pretrained
wget https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada/pretrained/ffhq.pkl
```

- [StyleGAN2-ada-pytorch 리포](https://github.com/NVlabs/stylegan2-ada-pytorch.git) 세팅
- 여러 pretrained 모델 중 ffhq.pkl 을 받을거임 ([전체 pretrained weights 리스트](https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada/pretrained/))
``` zsh
cd $PROJECT_ROOT
git clone https://github.com/NVlabs/stylegan2-ada-pytorch.git
cd stylegan2-ada-pytorch
mkdir pretrained && cd pretrained
wget https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/ffhq.pkl
```

