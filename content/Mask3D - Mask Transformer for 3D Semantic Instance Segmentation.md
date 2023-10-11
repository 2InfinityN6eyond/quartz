---
title: "Mask3D: Mask Transformer for 3D Semantic Instance Segmentation"
tags:
  - PAPER_REVIEW
  - COMPUTER_VISION
  - MACHINE_LEARNING
  - "#3D_INSTANCE_SEGMENTSATION"
---

```d2
plankton -> formula: will steal  
formula: {  
  equation: |tex  
    \\lim_{h \\rightarrow 0 } \\frac{f(x+h)-f(x)}{h}  
  |  
}

```

```d2

```


- Point Cloud 를 대상으로 함. Point Cloud 를 sparse한 voxel로 변환한 후 처리함.
- 처음으로 3D instance segmentation 분야에서 transformer를 이용해 SOTA를 달성함
	- instance queries 라는 것이 있음. 각 query는 scene 속 하나의 instance를  표현함. 이 instance query를 decode해서 instance feature도 얻고, 그 instance의 class label도 추정함.
- 기존 주류 연구들이 voting, clustering 등 거추장스러운 과정을 통해 instance mask를 얻는 것과 다르게 instance mask를 end-to-end 로 출력함.
	- Mask Module 이 instance mask prediction과 classification을 수행한다.
		- instance query와 point feature를 입력받음.
		- MLP를 통해 instance query를 instance feature로 decode하고, 이를 point feature 와 dot product를 시킴. 여기에 sigmoid를 취하면 heatmap이 됨 (instance query가 represent하는 instance의 heatmap)
		- heatmap을 0.5로 threashold를 취하면 instance mask를 얻음.
- instance mask를 predict했으면 이를 annotated mask 와 비교해 loss를 얻어야 한다. 이때 [[Hungarian Matching]] 을 이용한다.
-  Sparse Convolutional Feature Backbone Network
	- raw Pointcloud $P \in \mathbb{R}^{N \times 6}$  를 voxel $V \in \mathbb{R}^{M_0 \times 3}$ 로 변환함. 공간상의 모든 grid에서 voxel값을 구하는 것이 아님. 공간이 sparse 하기 때문에 몇개의 voxel만 계산함. 이때 voxel의 색은 그 안의 point들의 색의 평균임.
	- MinkowskiEngine 라이브러리의 (sparse한 3차원 공간 데이터를 처리할 때 주로 씀) UNet backbone을 이용해 다양한 스케일에서 feature를 구함.
	- $r \geq 0$ 인 $r$ 에 대해 $F_0 \in \mathbb{R}^{M_0 \times D}$ (full scale), $F_1 \in \mathbb{R}^{M_1 \times D}$ , ... 의 다양한 스케일의 피쳐맵 $F_{r}$ 를 출력한다.
	-  