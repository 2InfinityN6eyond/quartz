---
title: barrier
tags:
  - COMPUTER
  - SETUP
---
## Overview
- 여러대의 컴퓨터를 사용할 떄, 하나의 키보드/마우스로 다른 컴퓨터 역시 조적할 수 있도록 하는 프로그램이다.
- [위키 페이지](https://github.com/debauchee/barrier/wiki) . 원판인 [시너지]()의 [위키 페이지]()도 참조하면 좋을듯.
- synergy 의 오픈소스판 포크인 것 같다. 
	- synergy가 유료긴 한데, 소스는 공개되어 있어서 빌드만 할 줄 알면 쓸 수 있다.
	- 깃허브 찾아보면 누가  synergy 업데이트가 있을 때마다 빌드해서 릴리즈도 해놓음 ㅋㅋㅋ
	- 그런데 synergy를 빌드해서 썼을 때 barrier보다 나은지 모르겠음
- 하나의 데스크탑에 여러 개의 OS를 설치해도 각 OS에서 barrier를 똑같이 설정해주면 어느 OS로 부팅해도 동일하게 사용할 수 있어 편하다.

## 사용 방법
- SSL을 disable하자
- 클라이언트
	- 이름을 잘 기억해 놓아야 함.
- 서버
	- 클라이언트 컴퓨터의 이름을 config file의 이름으로 해야함.
	- ex) 클라이언트 컴퓨터 이름이 hjp-Z690-AERO-G  라면 config 파일을 hjp-Z690-AERO-G.config 로 저장해야 함.

## 문제 해결
### 특정 키 스트로크 전달 안됨
- macOS 서버에서 backtick/grave (\`) , tilde (~) 키 스트로크 전달이 안되는 치명적인 문제가 있다. 
	- 홈 디렉토리 갈때랑 마크다운에서 코드 임베딩할떄나 이래저래 개불편함.
	- 인터넷에 찾아보니 주로 맥에서 생기는 문제 같긴 하지만 macOS만의 문제는 아닌 것 같다. , 많은 사용자들이 공통적으로 겪고 있다.
	- 여러 해결책이 있었는데, 이게 제일 깔끔한 것 같다.
	- https://github.com/debauchee/barrier/issues/1531
		src/lib/platform/OSXKeyState.cpp 135번쨰 줄 { kKeyZenkaku, kVK_ANSI_Grave }
### 간헐적 끊김 문제
- 아직 명확한 원인과 해결책을 찾지 못함.


## etc
- nvidia GPU가 달린 ubuntu 컴퓨터를 barrier 클라이언트로 사용하고자 할 때, 반드시 GPU 드라이버를 제대로 설치한 후 barrier를 설정하자. 제발.
	- nvidia GPU가 달린 리눅스 컴퓨터는 클린 설치할 떄 아무것도 하지 말고 시스템 업데이트+GPU 드라이버 설치 를 가장 먼저 해야 한다. 무조건.