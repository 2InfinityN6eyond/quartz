---
title: obsidian_setup
tags:
  - SETUP
  - DIGITAL_GARDEN
  - COMPUTER
---

## 목적
- 내 obsidian 설정을 기록해둔다

## 노트 동기화
- iCloud Drive 이용
	- macOS, iOS 간의 동기화가 매우 편해진다.
		- macOS 에서 아래와 같은 경로에 iCloud Drive obsidian 폴더가 있을 것임
		``` bash
	/Users/$USER/Library/Mobile Documents/iCloud~md~obsidian/Documents/[Vault 이름]
```
	- Windows에서도 동기화하기
		- 아직 잘 안됨
	- Ubuntu에서도 동기화하기 
		- 아직 잘 안됨
- github 이용
	- .gitignore에 반드시 .obsidian/ 을 추가하자. 설정파일이 OS별로 달라서 꼬인다.

## 설정 동기화
- 

## Plugin
### Plugin 사용
- advanced tables
	- 표를 편하게 그릴 수 있도록 해준다
	- hotkey
- colored text
	- 텍스트 색을 설정할 수 있도록 해준다.
	- hotkey
		- color text
			- option + C
		- change color forward
			- option + shift + C
### Plugin 제작


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

