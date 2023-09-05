---
title: "barrier"
---

- synergy 의 오픈소스판 포크인 것 같다. 
- synergy가 유료긴 한데, 소스는 공개되어 있어서 빌드만 할 줄 알면 쓸 수 있다.
- 깃허브 찾아보면 누가  synergy 업데이트가 있을 때마다 빌드해서 릴리즈도 해놓음 ㅋㅋㅋ
- 그런데 synergy를 빌드해서 썼을 때 barrier보다 나은지 잘 모르겠더라.


- 데스크탑에 OS를 여러개 설치해도 각 OS에서 barrier를 똑같이 설정해주면 같은 노트북에 연결해서 아주 잘 쓸 수 있다.

- [위키 페이지](https://github.com/debauchee/barrier/wiki) . 원판인 [시너지]()의 [위키 페이지]()도 참조하면 좋을듯


- macOS 서버에서 backtick/grave (\`) , tilde (~) 키 스트로크 전달이 안되는 치명적인 문제가 있다. 
- 홈 디렉토리 갈때랑 마크다운에서 코드 임베딩할떄나 이래저래 개불편함.
- 인터넷에 찾아보니 주로 맥에서 생기는 문제 같긴 하지만 macOS만의 문제는 아닌 것 같다. , 많은 사용자들이 공통적으로 겪고 있다.
- 여러 해결책이 있었는데, 이게 제일 깔끔한 것 같다.
- 
- https://github.com/debauchee/barrier/issues/1531
	src/lib/platform/OSXKeyState.cpp 135번쨰 줄 { kKeyZenkaku, kVK_ANSI_Grave }


- 끊김 문제
	- 

- 우분투 클라이언트에서 마우스 포인터가 나타나지 않는 문제를 해결하기 위해 Wayland를 끄고 gdm3를 재시작했다. 그랬더니 2번째 모니터가 이상하게 출력되는 문제가 생겼다. 재시작하니 디스플레이 설정도 날라가고 이번엔 첫번쨰 디스플레이가 꺼진다. nvidia 드라이버가 없어서 그런가 싶다. 일단 드라이버를 깔아봐야겠음.
- 드라이버 버전은 오늘자 기준 535-server-open 을 추천한다. 그냥 지원이 1년 더 긴 차이인 것 같다. 
- sudo ubuntu-drivers autoinstall 했더니 문법 오류가 난다. 이게 뭔..?
- 너무 졸려서 그냥 안알아보고 수동으로 깔음
- sudo apt nvidia-driver-535-server-open

- 이번에는 /dev/nvme0n1p2:clean, ~~ blocks 이러면서 부팅이 안됨. 이 문제는 예전에 겪어봤던것 같다.
	- nvidia 드라이버 문제인가보다