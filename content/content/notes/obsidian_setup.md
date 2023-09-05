---
title: "obsidian_setup"
---

- 많은 노트 앱들이 있다. 비교해보자
	- obsidian
	- onenote
		- 체감상 동기화가 엄청 빠르다
	- margin note
		- 14일 무료체험기간에 써보려했는데 그동안 안써서 어떤지 잘 모름. 너무 비싸서 결제를 못하겠음 - 창업지원금으로 해볼까?
	- upnote
		- null
	- goodnotes
		- PDF에 필기하기 좋음
		- 일기랑 플래너를 씀
			- 이래저래 다른 앱을 써봐도 결국 아날로그틱한걸로 돌아오게 되더라
	- notes (애플 기본앱)
		- 끄적이기용으로 좋음

- 너무 산만해져서 잘 통합해봐야 되는데... 그게 쉽지가 않다.


- obsidian
	- 맥-아이폰-아이패드 간 동기화 (아이클라우드 드라이브 이용)
	- 맥에서 vault를 만들 때 아이클라우드 드라이브 디렉토리에 만들면 된다.
		- 아마 옵시디언에서 icloud 동기화를 켰으면 이 디렉토리가 있을텐데 이 안에 넣으면 된다.
		```/Users/$USER/Library/Mobile\ Documents/iCloud\~md\~obsidian/Documents/```
		- 그러니까 USER명이 hjp이고 valut 이름을 posts로 하고 싶으면
		```/Users/hjp/Library/Mobile\ Documents/iCloud\~md\~obsidian/Documents/posts```

	- 다른 os와의 동기화는 깃으로 하면 된다. 이때 .gitignore에 .obsidian/ 을 꼭 추가해줘야 한다. 운영체제별로 옵시디언 설정파일이 다른 것 같다.

	- OS간 옵시디언 설정을 동기화하는 법
		- macOS - iPadOS - iOS
		- macOS-Linux-Windows