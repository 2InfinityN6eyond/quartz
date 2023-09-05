---
title: Diffusion and Score Based Generated Models
tags:
  - MACHINE_LEARNING
  - GENERATIVE_MODEL
  - PAPER_REVIEW
---

generative model을 만들기 위해서는 데이터의 probability distribution을 알아야 함. 
데이터의 distribution을 직접 알긴 힘드니 모델링함 

image 같은 데이터의 distribution은 아주 복잡하지.
이걸 모델링하려면 어떻게 할까?
뉴럴 네트워크로 한다.


인풋 데이터 샘플을 받아서 확률값 스칼라를 뽑는거지.
하지만 이러면 음수가 나올 수 있으니까 exp를 취하고 normalized constant Z로 나누자.
Z : 총합. 하지만 이걸 계산하는건 현실적으로 어려움.

intractable한 normalized constant를 tracking하는 방법들
1. enegy based model
2. using restricted neural network models
3. probability를 모델링하지 않고 generation process만 모델링하기
	- GAN

score function으로 

p(x) : pdf

score function : 

score funtion을 알면 적분을 통해 density function을 알 수 있음.
그리고 score function이 더 쉬움.,

normalized constant를 추적하지 않기 때문.


score Model $s_\theta(X) : R^d->R^d$ 

fisher divergence 를 이용해 loss를 구할 수 있음.
하지만 score function을 모름.
score matching은 fisher divergent 와 equivalant함.

$E_{Pdata}{(x)}[1/2 || s_\theta(x) || + trace(\nebula x  ) ]$ 



