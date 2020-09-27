---
layout: post
title:  "[Tip] github 사용법 - Fork&PR"
subtitle:   "github 사용법 - Fork&PR"
categories: tip
tags: github git
comments: true
header-img:
---



### 지난 포스팅

[1. 마크다운 문법](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-Markdown/)

[2. github 가입 및 다운로드](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-githup_signupsetup/)

[3. git bash shell 명령어](https://lhmlhm1111.github.io/tip/2020/09/21/Tip-Tip-Shellcommand/)

[4. git 사용법 - 코드 관리(SCM) & 버전 관리(VCS)](https://lhmlhm1111.github.io/tip/2020/09/22/Tip-Tip-git/)

[5. github 사용법 - push&pull](https://lhmlhm1111.github.io/tip/2020/09/23/Tip-Tip-github_pushpull/)

[6. github 사용법 - Branch&PR 1편](https://lhmlhm1111.github.io/tip/2020/09/24/Tip-Tip-github_branchPR1/)

[7. github 사용법 - Branch&PR 2편](https://lhmlhm1111.github.io/tip/2020/09/25/Tip-Tip-github_branchPR2/)

---



지난 포스팅에서는 `github`의 협업 시나리오 중 하나인 **Branch & PR** 모델에 대해 알아봤습니다. 이번 포스팅에서는 **오픈 소스** 프로젝트에서의 협업 모델인 **Fork & PR** 모델에 대해 알아보겠습니다.

지난 포스팅 말미에 짧게 언급했듯 **Branch & PR** 모델은 업계에서 표준 협업 방식으로 채택하고 있는 아주 효율적인 협업 모델입니다. 하지만 **오픈 소스**의 위력이 대두되는 현 시점에서 일부 Collaborator 이외에는 프로젝트에 기여할 수 없는 모델이라는 한계점을 가지고 있습니다. 이러한 문제점을 보완하기 위한 협업 모델이 **Fork & PR** 모델입니다. **Fork & PR**  방식을 이용한다면 우리가 잘 알고 있는 "Pandas" 같은 모듈에도 직접 기여를 할 수 있습니다. Collaborator가 아닌 외부의 기여자를 **Contributor**라고 부릅니다.

이번에도 계정이 두 개가 필요합니다. 지난 번처럼 한 계정으로는 원격 저장소를 생성해주세요. 프로젝트에 팀원으로 속해 있는 Collaborator 역할을 맡을 것입니다. 다른 한 계정은 프로젝트에 소속되어 있지 않지만 오픈 소스 프로젝트에 기여하고 싶은 Contributor의 역할을 맡으시면 됩니다. 이번에도 3행시를 짓는 오픈소스 프로젝트를 진행해봅시다. [지난 포스팅](https://lhmlhm1111.github.io/tip/2020/09/24/Tip-Tip-github_branchPR2/)을 참고하여 똑같이 만들어 주세요.

![image-20200926194021939](https://user-images.githubusercontent.com/47618340/94341733-bb98dc00-0046-11eb-9371-0b6eae76fa9d.png)

---

이제 Contributor가 되어 봅시다. 로그인 해서 좌측 상단에 있는 검색창에 원격 저장소를 검색해주세요. 저의 경우는 lhmlhm1111/collabo2 라고 검색하면 들어갈 수 있겠네요.

<img src="https://user-images.githubusercontent.com/47618340/94341738-cb182500-0046-11eb-9528-e1d5ec44a9cb.png" alt="image-20200926194623299" style="zoom:50%;" />

---

Collaborator로 지정되어있지 않기 때문에 해당 원격 저장소에 직접 `push/pull`을 할 권한이 없습니다. 대신 원격 저장소를 **포크**로 푹 찍듯이 자신의 계정으로 복사해 가져올 수 있습니다. 우측 상단에 `Fork` 버튼을 클릭합니다.

![image-20200926210319044](https://user-images.githubusercontent.com/47618340/94341751-e1be7c00-0046-11eb-9d07-e11048285648.png)

---

잠깐의 로딩을 기다리면 자신의 계정으로 원격 저장소가 생성된 것을 알 수 있습니다. 자세히 보시면 **forked from lhmlhm1111/collabo2**라고 적혀있는 것을 확인할 수 있습니다. 해당 저장소를 `pull`하여 자신의 로컬저장소로 가져와 수정한 후 다시 push 해줍니다. 이 과정은 생략하겠습니다.

<img src="https://user-images.githubusercontent.com/47618340/94341755-ed11a780-0046-11eb-89ac-c26447f70717.png" alt="image-20200926210512881" style="zoom:50%;" />

(혼자 하시는 분들의 경우 git bash에 등록되어 있는 계정이 달라 Push가 안되는 현상이 발생합니다. 실제 상황에서는 한 로컬에서 계정을 번갈아 Fork & PR을 하는 경우는 거의 없지만 그래도 연습 해보고 싶은 분들은 [여기](https://somjang.tistory.com/entry/Git-Git-Bash-%ED%84%B0%EB%AF%B8%EB%84%90-%EA%B3%84%EC%A0%95-%EB%B3%80%EA%B2%BD-%EB%B0%A9%EB%B2%95)를 참고하셔서 git bash에 등록된 계정을 바꿔주시고 실행해주세요.)

---

수정이 잘 됐다면 좌측 상단의 Pull requests를 누릅니다.

![image-20200926214427799](https://user-images.githubusercontent.com/47618340/94341763-00bd0e00-0047-11eb-8376-f9dfd6f94f72.png)

---

우측 상단의 New pull request를 눌러줍니다.

![image-20200926215234502](https://user-images.githubusercontent.com/47618340/94341771-1d594600-0047-11eb-8d8f-01333ee67e7a.png)

---

다시 한 번 우측 상단에 뜨는 Create Pull request를 눌러줍니다

![image-20200926215430888](https://user-images.githubusercontent.com/47618340/94341777-29dd9e80-0047-11eb-9898-0d3c2e02e2db.png)

---

제목과 설명을 작성한 후 Creat pull request를 클릭하면 **PR**이 완료됩니다.

![image-20200926215806092](https://user-images.githubusercontent.com/47618340/94341784-395ce780-0047-11eb-887a-61db35443cdf.png)

---

 이제 팀장의 계정으로 가봅니다. Pull requests가 하나 들어와 있는 것을 확인할 수 있습니다. 클릭해봅시다.

![image-20200926220133574](https://user-images.githubusercontent.com/47618340/94341796-51346b80-0047-11eb-843b-f383262c0acb.png)

---

지난 포스팅에서 봤던 것과 똑같은 화면이 나옵니다. 마음에 들면 Merge pull request를 누르시고 마음에 들지 않으면 Close pull request를 선택해주세요.

![image-20200926220739013](https://user-images.githubusercontent.com/47618340/94341800-614c4b00-0047-11eb-9b00-cf888b665fae.png)

---

잘 된 것을 확인할 수 있습니다.

![image-20200926220930293](https://user-images.githubusercontent.com/47618340/94341807-6d380d00-0047-11eb-924d-6f4cb8ef748c.png)

---

이번 포스팅을 끝으로 `github` 사용법에 대한 포스팅을 마치도록 하겠습니다. 여기까지만 잘 숙달하신다면 협업 상황에서 별다른 무리 없이 `github`를 사용하실 수 있을 것입니다. 

다음 포스팅은 보너스로 `github` 블로그를 구축하는 방법에 대해서 다뤄보도록 하겠습니다. 읽어주셔서 감사합니다~

---



---

### 다음 포스팅

[github 블로그를 만들자!](https://lhmlhm1111.github.io/tip/2020/09/27/Tip-Tip-github_blog/)

