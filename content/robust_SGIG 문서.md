

- Table 1 보충실험
	- 결과
	- 
		| dataset      | swin transformer | lee.at.al | AudioCLIP | Wav2CLIP | resnet |
		| ------------ | ---------------- | --------- | --------- | -------- | ------ |
		| ESC50        | 0.627            | 0.314     | 0.242     |          |        |
		| UrbanSound8k | 0.525            | 0.205     |           |          |        |
		| VGGSound     | 0.686            | 0.461     |           |          |        |
		| AudioSet     | 0.271            | 0.163     |           |          |        |

	- metric
		- mAP
			- 주로 object detection에 사용
		- accuracy
			- 
	- dataset
		- AudioSet
		- VGGSound
		- ESC50
		- UrbanSound8K
	- 모델 세팅
		- Swin Transformer (with audio-visual weakly supervised contrasive learning)
			- 224x224 크기의 이미지를 입력함.
		- lee at.al.
			- 512x128 크기의 이미지를 입력함.
		- Wav2CLIP
			- 저자들이 raw Audio를 어떻게 입력시키는지 정보를 제공하지 않음.
				- Audio Encoder인 model.encoder.ResNetExtractor 는 model.resnet.ResNet 를 ResNetExtractor.encoder 멤버변수로 가지고 있음.
				- ResNet 클래스는 torchaudio.transforms.Spectrogram 타입의 ResNet.spectrogram 을 멤버변수로 가지고 있음
				- ResNetExtractor.forward()가 호출되면 
				- ResNet.forward() 를 호출할 때 ResNet.spectrogram() 을 먼저 수행함.
				- 
		- AudioCLIP
			- pretrained model, 원본 CLIP에 있는 파일을 GIT LFS로 제공하는데, 파일이 다운로드되지 않음.
			- 저자들이 공개한 코드는 CLIP 코드를 상속받아 CLIP 속에 Audio Encoder를 통합해 놓음. 하지만 저자들이 사용한 CLIP 코드가 작동되지 않아 Audio Encoder만을 떼어내고, 전체 pretrained weights 중 오디오 인코더 부분을 분리하여 사용함.
			- 저자들이 제공하는 Audio Encoder의 embedding space는 1024차원임.
			- CLIP 에서 제공하는 모델 별 embedding space는 다음과 같음
				| model_name     | embedding space dimension |
				| -------------- | ------------------------- |
				| ViT-B/32       | 512                       |
				| ViT-B/16       | 512                       |
				| ViT-L/14       | 768                       |
				| ViT-L/14@336px | 768                       |
				| ViT-B/16       | 512                       |
				| RN101          | 512                       |
				| RN50x4         | 640                       |
				| RN50x16        | 768                       |
				| RN50x64        | 1024                      |
				| RN50           | 1024                      |
			- AudioCLIP 의 AudioEncoder의 성능을 평가할 때에는 CLIP 의 pretrained model 중RN50을 이용함.

- Landscape, Wallpainting 도메인의 StyleGAN2 generator를 이용하여 실험.
	- WikiArt pretrained StyleGAN2 Generator
		- 

- Style Mixing
	- 동일한 원본 StyleGAN2 latent code에 대해, sound guided latent code optimization, text guided latent code optimization을 수행하여 두 개의 latent code $l_a$  $l_w$  를 구한다.
	- StyleGAN2의 latent code는 $L \cross D$  차원인데, 각 행벡터들이 이미지 속 특징들을 결정하고, 개별 행벡터들이 이미지의 특징에 미치는 영향은 disentangle 되어있기 때문에 $l_a$, $l_w$ 의 latent code의 행벡터들을 선택적으로 조합해 새로운 latent code를 얻을 수 있다.
	- 실험 설정
		- Genertor, 주제 설정
			- 원하는 이미지를 얻기 위해 우선 StyleCLIP을 이용해 원하는 이미지의 latent code를 얻은 후, sound-guided manipulation, text-guided manipulation을 진행하였다.
				- landscape
					- 비오는 소리 + 텍스트 “노을”
					- 불나는소리 + 텍스트 ”구름낀 날씨“
				- 동물
					- 짓는 소리 + 텍스트 “발라당 드러누움”
				- 사람
					- ㄴㅇ
				- WallPainting
					- 
		- Sound Guided
			- 
		- Text Guided
			- .
			- 
		- Style Mixing
			- 수작업으로 수행


	| dataset      | swin transformer | lee.at.al | AudioCLIP | Wav2CLIP | resnet |
	| ------------ | ---------------- | --------- | --------- | -------- | ------ |
	| ESC50        | 0.627            | 0.314     | 0.242     |          |        |
	| UrbanSound8k | 0.525            | 0.205     |           |          |        |
	| VGGSound     | 0.686            | 0.461     |           |          |        |
	| AudioSet     | 0.271            | 0.163     |           |          |        |

mAP

| dataset      | swin transformer | lee.at.al | AudioCLIP | Wav2CLIP |
| ------------ | ---------------- | --------- | --------- | -------- |
| ESC50        | 0.627            | 0.314     | 0.512     | 0.422    |
| UrbanSound8k | 0.525            | 0.202     | 0.410     | 0.365    | 
| VGGSound     | 0.689            | 0.461     | 0.492     | 0.449    |
| AudioSet     | 0.271            | 0.133     | 0.241     | 0.184    |

accuracy_score

| dataset      | swin transformer | lee.at.al | AudioCLIP | Wav2CLIP |
| ------------ | ---------------- | --------- | --------- | -------- |
| ESC50        | 0.613            | 0.482     | 0.452     | 0.398    |
| UrbanSound8k | 0.511            | 0.341     | 0.319     | 0.302    |
| VGGSound     | 0.631            | 0.503     | 0.342     | 0.326    |
| AudioSet     | 0.315            | 0.205     | 0.160     | 0.133    |


mAP


accuracy_score


| dataset      | swin transformer | lee.at.al | Wav2CLIP | 
| ------------ | ---------------- | --------- | -------- | 
| ESC50        | 0.613            | 0.482     | 0.142    | 
| UrbanSound8k | 0.511            | 0.341     | 0.401    | 
| VGGSound     | 0.631            | 0.503     | 0.121    | 
| AudioSet     | 0.315            | 0.205     | 0.102    | 
