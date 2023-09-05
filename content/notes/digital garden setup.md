---
title: "digital garden setup"
tags:
- "DIGITAL_GARDEN"
- "SETUP"
---


## 1. 개요
이 블로그를 어떻게 만들었고, 어떻게 가꾸었는지에 대해 정리한다.

- 블로그 컨탠츠는 [obsidian](https://obsidian.md/) 을 이용해 작성한다.
	- [나의 obsidian 이용법](./obsidian_setup.md)
- 호스팅은 나의 [quartz](https://github.com/jackyzha0/quartz) 를 기반으로 추가 개발하여 이용하고 있다.
	- quartz는 obsidian으로 작성한 마크다운들을 잘 파싱해서 깃허브 페이지에 띄울 수 있도록 하는 static page generator이다.
	- hugo-obsidian (quartz 저자가 개발), hugo를 이용한다.
- 나는 [quartz fork](https://github.com/2InfinityN6eyond/quartz)를 계속 개조하고 있다. 언젠가 다른 것으로 바꿀 수 도 있다.

- 만약 독자께서 quartz를 이용해서 블로그를 만드는 것에 관심이 있다면, 우선 [공식 가이드](https://quartz.jzhao.xyz/#get-started) 를 따라하는것을 추천드립니다.


## 2. 블로그를 연 과정

- 블로그를 시작한 계기
	- 지금부터라도 체계적으로 기록을 남겨야겠다고 생각함
- 툴 선정 계기
	- obsidian
		- 2020년 10월쯤에 탭/컨텐츠 사이의 관계를 시각적으로 표현할 수 있는 웹 브라우저에 대한 아이디어를 떠올렸지만, 의지박약으로 아직까지 개발을 못했다... 내 전문분야가 아니기도 하고..
			- 그때는 회사를 다니고 있어서 개발할 시간이 부족했고,
			- chromium embedded framework
			- 크로뮴을 기반으로 빌드하거나,  또 iOS, ipadOS 를
		
		- UI 설계도 어려웠고 구현도 어려웠다. 프로그램 뿐만이 아니라 
		
		- 같이 하자고 하는 친구가 있었지만, 나도 그렇고 끈기가 부족해서 만족할만한 결과물이 나오지 못했다.
		- 이후에 chatGPT같은 서비스들이 나오면서 사용자가 직접 탭들을 관리하면서 내용을 이해하는 것보다 AI가 정리해서 떠먹여주는 방식이 대세가 될 수도 있겠다는 생각이 들어서 열정이 식었다. 
		
		
		- 2021년 쯤 유튜브에서 우연히 obsidian을 알게 되었고, 가장 많이 쓰는 메모 프로그램이 되었다.
			- 여러 페이지들을 유기적으로 관리하기보다 탭으로 관리하는 것은 기존 프로그램들과 같지만, graph view가 예전 아이디어와 비슷한 점이 있었다.
			- 로컬 기반이어서 자유도가 높고, 설정을 많이 건드릴 수 있고, 플러그인을 쓸 수 있는 점이 좋았다.
	- quartz
		- 블로그도 obsidian의 UI랑 비슷하게 할 수 있는 방법을 찾다가 유튜브에서 영상을 통해 quartz를 알게 되었다.
		- 그동안 프론트엔드와의 접점이 전혀 없었는데, 블로그 운영하면서 조금씩 해보는것도 좋을 것 같다.

- 기본 세팅
	- 우선 처음에는 quartz의 공식 가이드를 그대로 따라했다. **토씨하나 안틀리고** 따라하는걸 추천.
		- [Step 3: How to setup your Obsidian Vault to work with Quartz](https://quartz.jzhao.xyz/notes/obsidian/) 는 일단 스킵하자.
			- 옵시디언으로 마크다운을 관리하는 방법에 대한 가이드인데, 일단 필요없다.
			- 중요한 것은 마크다운을 작성할 때 frontmatter를 충실하게 달아야 한다는 점이다.
				- 어차피 frontmatter 잘 관리하는게 나한테 좋다.
		- 2023.06.15 기준 m2 max 맥북에 hugo extended를 깔았는데 hugo-obsidian이 에러를 뱉는다.
			- 윈도우 11 에서는 잘 되길래 윈도우에서 했다. 당분간 블로그 관리는 윈도우에서 하는걸로.
				- 윈도우를 쓴다면 choco 강추합니다. [윈도우 세팅 정리]()
	- obsidian 연동법
		-  [내가 obsidian을 사용하던 방법]()
		1. 블로그용 vault를 새로 판다. 이름은 content로 짓는 게 좋다. 아니어도 상관없음
			- 나는 동기화를 위해 vault를 항상 깃 리포로 만든다.
				- [모든 주요 OS간 vault를 동기화하는 법 ]() 참조
				- [모든 주요 OS간 obsidian 세팅 동기화하는 법]() 참조
			- obsidian에서 자주 쓰는 플러그인 중에는 hugo가 해석하지 못하는 구문을 만드는 애들이 많기 때문에 블로그 포스팅용 vault를 새로 파는걸 추천한다.
		- quartz는 $QUARTZ_ROOT/content/ 내부의 모든 마크다운을 재귀적으로 읽어서 웹페이지를 만든다.
			- content/ 말고 다른 디렉토리를 지정할 수는 없나 하고 시도해봤는데 안된다.
				- MakeFile의 make serve에서 content/ 말고 다른 디렉토리를 지정하면 뭔가 꼬인다.
		- 따라서 그냥 git submodule로 vault를 $QUARTZ_ROOT/content/ 밑에 가져다 놓으면 되지 않나 라고 생각할 수 있다.
			- 단순히 복붙하면 안된다. quartz가 깃 리포토리이고 vault 역시 동기회를 위해 git 리포지토리이기 때문.
				- nested git repository는 submodule을 이용해야만 한다.
			- git submodule 대신 content/ 안에 valut의 symbolic link 를 걸어봤는데, 안된다.
				- 어차피 깃허브에 마크다운이 올라가야 깃허브 액션에서 웹페이지로 빌드될 거기 때문에 심볼릭 링크로 될 리가 없다.
		- 그런데 이렇게 하면 quartz가 (정확히는 hugo-obsian이) 마크다운 속 obsidian 스타일 링크를 제대로 파싱을 하지 못한다.
		- 결과적으로 quartz의 기본 content/ 디렉토리를 지워버리고, vault를 content 라는 이름으로 그 자리에 놓는게 제일 마음이 편한 것 같다.
			- 일단 바로 지워버리지 말고 이후 스텝으로 갑시다
			- vault가 깃 리포라면  $QUARTZ_ROOT/content/ 로 그냥 복붙해버리면 안됩니다. 
		2. content/ 내부에 있는 내용물들을 vault 내부로 복붙한다.
			- \_index.md는 블로그 홈페이지이고, templates/는 블로그 렌더링을 위해 필요하다.
			- content/notes/ 는 필요없다.
		3. quartz에서 content/ 디렉토리를 지운다.
		4. vault를 quartz로 submodule한다.
			- cd $QUARTZ_ROOT
			- git submodule add \[vault 깃허브 링크] content/
		5. github action workflow에서 submodule을 업데이트하는 과정 추가
			ㅁㄴㅇㄹ
		6. 포스팅 작성 시 자동으로 업데이트하도록 설정
			
		- 이렇게 해서 세팅이 끝났다.
		- 
	- 포스트 업데이트 방법
		1. obsidian으로 포스트를 작성한다.
		2. 커밋하고 vault의 origin에 푸시한다.
		3.  $QUARTZ_ROOT/content/ 로 가 pull 한다.
		4. quartz를 커밋하고 origin에 푸시한다.

	- 방법이 번거롭긴 하지만, 블로그 컨텐츠 vault와 블로그 웹페이지 제너레이터를 위한 리포를 따로 관리하는 것은 합리적이다.

	- frontmatter를 항상 신경써서 작성하자.
	- 포스트를 수정하면 항상 로컬에서 제대로 작동하는지 확인하자. 나중에 깨졌을때 어디서 깨졌는지 찾기 어려울것같다.
	- 깃허브 페이지 빌드하는게 엄청 오래걸린다.



	- 
		- quartz가 마크다운 내의 링크를 파싱할 때 링크의 path가 vault의 루트 디렉토리부터 시작해야 하지만, obsidian이 그런 path 방식을 지원을 안하는 것 같다.
			- 예를 들어 vault 이름이 posts 이고 
		
		- , vault에 해당하는 디렉토리를 $QUARTZ_ROOT/content/ 안에 복붙해서 넣으면 링크가 다 깨진다.
		- 



- quartz는 obsidian으로 포스팅을 작성하는걸 권장한다. 애초에 개발 동기가 "obsidian의 graph view를 웹에 올리자" 인 것 같다.
		- **obsidian vault에서 파일을 디렉토리 계층으로 관리하지 않고, 그냥 쭉 펼처놓은 다음 tag를 적극적으로 사용하는 방식을 상정한 듯 하다.**
			- 이렇게 하는게 좋다. 이유는 아래에 나와있음.
			- 이렇게 하지 않아도 별 문제는 없다.
				- graph view에서 파일의 absolute path를 보여주기 때문에 불편할 수 있다 정도?


## 3. quartz 분석
| 웹개발에 대해 잘 모르기 때문에 qurtz를 뜯어보면서 웹 공부도 좀 해보고 해야한다.

정규식이 엄청 많다. 암기할것도 많아서 프런트엔드는 AI도움없이는 힘들듯.

- 개발자인 [Jacky Jhao](https://github.com/jackyzha0) 는 엄청 대단하신 분인것같다. [본인의 digital garden](https://jzhao.xyz/) 을 가꾸신 것 보면 존경심이 든다. 부럽다.
	- [quartz로 만든 웹페이지들의 쇼케이스도 있다](https://quartz.jzhao.xyz/notes/showcase/). 다들 엄청나다. 정원이 무슨 국립공원임
- 마크다운 처리에 hugo를 이용한다. obsidian 스타일의 링크를 처리하기 위해 hugo-obsidian 을 직접 개발했다고 한다.
- 일단 hugo-obsidian은
	- obsidian으로 쓴 마크다운 파일들을 읽어와 옵시디언 스타일의 링크를 분석해서 
- hugo는
	- 마크다운을 웹페이지 문서로 바꿔준다.
- quartz는 
	- static webpage.
	- semantic search 지원
	- github action 을 통해 웹 호스팅을 한다.


- quartz의 저자는 개별 메모를 디렉토리에 분류해 넣지 않고 일단 쫙 뿌린 다음에 태그랑 파일간의 링크를 이용해 관리하는 것을 지향하는 것 같다.
	- 보통 메모장을 관리할 때 디렉토리 계층구조를 이용해서 정리한다. 나도 그렇게 해왔다.
		- 보통 컴퓨터의 파일시스템은 트리 구조이다. 디렉토리 파일은 intermediate node이고 개별 파일이 leaf node이다.
		- 하드링크를 이용하면 그래프 처럼 쓸 수 있긴 하지만, 디렉토리에 하드링크를 잘못 쓰면 loop이 생길 수도 있어서 보통 OS에서 하드링크는 파일만 되게 막는다.
		- 심볼릭 링크를 쓰면 유사 그래프 구조가 된다고 볼 수도 있다. (맞나? 잘 모르겠음 나중에 찾아봐야함)
	- 하긴 생각해보면 메모장은 내 생각을 관리하려고 쓰는건데 굳이 디렉토리 트리 구조에 갇힐 필요가 없긴 하다. 그게 관리가 편하고 익숙해서 그렇지.
	- 태그를 통해 관리하면 파일과 그 파일의 분류 간의 논리적 구조를 그래프로 나타낼 수 있기 때문에 트리 구조인 파일시스템 방식보다 훨씬 유연하기도 하다.
	- 디렉토리 구조로 관리하려면 파일을 만들 때 먼저 이미 있는 디렉토리로 분류해야 돼서 내용을 거기에 끼워맞추게 되는데 태그 방식으로 하면 훨씬 유연할 것 같다.
- 파일간의 관계는 링크와 백링크를 통해, 파일과 그 파일이 속하는 논리적 개념 사이의 관계는 태그를 통해 표현한다.
- 하지만 그런 방식을 쓰면 어떤 내용에 대한 파일을 찾으려고 할 때 기존 방식대로 디렉토리를 타고 들어가서 보는 것이 불편할 수 있다.
- 그래서 quartz가 태그랑 semantic search 지원이 강한 것 같다.
- 나도 로컬에서 작업할 때 옵시디언에서 태그를 거의 안썼는데, 태그 위주로 사용하는 법을 찾아봐야겠다.
- 이렇게 했을 때 같은 이름의 파일을 두 개 이상 생성할 수 없다는 문제가 생길 수도 있을 것 같다. 근데 큰 문제는 아닐듯.


	- 파일을 디렉토리에 적절히 트리 구조로 분류해 저장하기보단, 한 계층에서 파일들을 죄다 흩뿌려놓고, 파일들 간의 논리적 관계를
	- 사실 이렇게 하면 

	- 개별 파일을 leaf node로 봤을 때 로컬에서 디렉토리 계층구조에 파일을 잘 분류해서 보관하는 방법은 트리 구조를 쓰는 것이다.

	- 또 디렉토리는 이렇게 봤을 때 중간노드라 별 컨텐츠가 없기 때문에 


	- 그래서 semantic search를 잘 갖춰놓고 tag 를 잘 지원하는 것 같다. 다렉토리 방식도 논리적으로 보면 이런 방식의 부분집합이다. tag가 더 자유롭긴 하다. 그래프가 가능하기 때문에



## 4. quartz 개조
아직은 계획


### 0. 간단한 것들

- quartz를 건드리는 게 아니라 단순히 포스트를 업데이트할 때 하는 git commit에서 커밋메시지에 posts 리포의 쌓인 그동안의 커밋메시지를 추합해서 넣고 싶다.

- 

### 1. 인터렉티브한 tag 시스템 UI
태그 가지고 파일의 내용을 논리적으로 분류하는건 좋은데, 존재하는 태그들의 목록이나 태그 끼리의 관계, 특정 태그에 해당하는 포스트 들을 찾는게 엄청 불편하게 되어있다.


### 2. interactive graph를 더 인터렉티브하게 하기
기본 quartz 그래프는 별로 interactive 하지 않다.


### 3. 댓글


### 4. 광고


### 5. 마크다운 밖의 리소스(?) 관리
포스트에서 이미지나 영상 같은 외부 자료를 많이 사용하는데, 예내들도 그래프 구조로 관리할 수 있으면 좋겠다.

### 6. 다중언어 지원
영어로도 써서 올리고 싶음
검색엔진에 더 잘 노출될 수 있는 법도 고민해봐야겠다.


### 파이썬 3D 그래픽 삽입법


-------------
- 개인 디지털 가드닝에 대해 정리한다.
- 로컬 노트는 [[obsidian_setup]] 이용. 웹페이지로 띄우는 것은 quartz 이용

- 노션이 단순 마크다운에 GUI를 이용한 기능을 더해서 좀더 하이레벨하게 쓸 수 있긴 하지만 블로깅용으로 obsidian은 충분히 괜찮은 것 같다.

- hugo, hugo-obsidian, quartz를 보면서 간단하게 자바스크립트 공부도 해보고 좋지뭐
- 파이썬 코드 임베딩, 옵시디언 플러그인 임베딩 등


- hugo가 마크다운을 해석할 때 좀 빡빡하게 군다.
- 옵시디언 플러그인이 있거나 해서 해석이 안되는 부분이 있으면 빌드가 안되는건지


- 일단 macOS 2023년 기준으로 왜인지 hugo-extended 를 깔았는데도 로컬에서 서버가 안뜨고 에러가 난다. 

- 중요한 일은 아닌 것 같으니 그냥 윈도우에서 하고 나중에 찾아보자.


- 아주 중요함. 마크다운 파일이 비어있어도 frontmatter가 없다고 에러가 막 난다.
- 리모트에 푸시하기 전에 꼭 로컬로 빌드가 되는지 확인을 하자.
- 이왕 깐깐하게 할거 frontmatter로 파일 잘 관리해보자


- 일단 옵시디언 vault를 깃 리포로 하나 파서 맥북-데탑 동기화를 하게 했다.
- 맥-아이패드-아이폰은 아이클라우드로 동기화할 수 있다. 이렇게 하려면
- 
- submodule을 쓸 수도 있지만... 그냥 로컬에서 심볼릭 링크 하나 파는게 더 나은듯


- ㄴㄴ 그냥 submodule 쓰자. .git이 nest되어서 문제 생길수도.

- 

- $QUARTZ_ROOT_DIR/content/notes/ 안에 놔야 인식을 하는 것 같다. 그 안에서는 디렉토리로 계층을 놔도 잘만 되는 듯.

- 어차피 로컬 서버는 윈도우에서만 되니까 posts를 쓴 다음에 깃으로 동기화하고 로컬 quartz 폴더 안에서 make serve 로 잘 되는지 테스트 후에 푸시하자.



- $QUARTZ_ROOT/content 안에 있는 모든 디렉토리의 마크다운 파일을 다 빌드하는 것 같다.
- 하지만 심볼릭 링크를 타고 가지 않는 것 같다. 하드링크를 박아야 하나..
- 깃헙에 올릴때 마크다운이 같이 올라가야 하나? 그러면 심볼릭 링크로 하면 안될거고 아니면 심볼릭 링크로 해도 될듯.
- -> 그런데 깃헙 액션으로 빌드하기 때문에 깃허브 리포에 모든 마크다운이 올라가야 한다. 심볼릭 링크 말고 하드링크를 걸어야함.
- 