---
title: mind web
tags:
  - ideas
  - PROJECT
---

- 아이디어
	- 웹 페이지, PDF 등의 파일 뷰어/편집 프로그램에서 파일들 끼리 가지는 그래플 구조의 연관관계를 시각적으로 보여주고 직관적으로 사용할 수 있는 프로그램 개발
- 필요성
	- 웹 브라우저, PDF 리더, IDE 처럼 어떠한 컨텐츠를 보여주는 애플리케이션 프로그램들을 사용할 때에는 여러 컨텐츠를 동시에 보는 경우가 있다.
	- 이런 프로그램들에서 여러 컨텐츠를 동시에 보여줄 때에는 '탭' 을 사용한다.
	- 많은 경우에 컨텐츠들은 서로 간의 관계를 가진다.
		- 예를들어 학술 논문의 경우 참조논문들과의 연결관계가 있다.
		- 웹페이지에서 하이퍼링크로 다른 웹페이지에 의존하는 경우가 많다. 특히 위키백과 같은 것들
		- 쇼핑을 할 때에도 하나의 웹페이지에서 연결되는 여러 웹페이지를 동시에 봐야 할 때가 많고 유튜브를 볼 때에도 그런 경우가 많다.
	- 탭은 컨텐츠를 단순히 나열하는 것이기 때문에 이러한 컨텐츠간의 연결 관계를 전혀 반영하지 못한다.
	- 따라서 사용자가 컨탠츠 간의 논리적인 관계를 시각적으로 파악할 수 있고, 컨텐츠들이 가지는 이러한 특징을 잘 반영할 수 있는 UI가 있으면 좋겠다.
- UI 설계
	- 그래프 구조를 보여주는 UI 요소
		- 
	- 컨텐츠 뷰어
		- 그래프 구조에서 
- 구현
	- 요구사향
		- PDF 파일, 웹 문서 서로간의 링크를 파싱할 수 있어야 한다.
	- 웹 엔진
		- chromium
			- 사실 거의 유일한 옵션이 되는 것 같다.
		- servo
			- 개발 중단된 것 같음..
			- gecko도 사용하기에 애매하다
		- webkit
			- iOS에서 지원하는 유일한 브라우저
			- 문서가 너무 부실하고 오래됨. 빌드도 쉽지 않음
			- firefox iOS 앱 소스가 공개되어 있어 봤는데 기본 웹킷 소스랑 엄청 다른 것 같다. 쉽지 않을듯..
		- 추상회된 프레임워크들
			- chromium embedded framework
			- webview
			- Qt
				- 라이센싱이 복잡함..
	- 웹 문서의 경우 하이퍼링크 부분과 다른 문서와의 엣지를 연결할 때 html 엘리먼트를 건드려서 시각적으로 표현할 수 있다.
	- pdf 같은 경우에는 어떻게 할 지 모르곘음.
	- OS  사이 동기화 지원


- UI가 핵심인 프로그램이라 프런트엔드 개발 느낌이 찐하게 나는데 프론트엔드쪽으로 갈 것도 아니고 인공지능쪽 공부하기도 시간이 부족해서 정체가 심하다..
- 웹브라우저 가지고 UI 바꾸는 것도 쉽지 않다.
- 웹, 로컬 사이의 벽을 허물어야 함
- 