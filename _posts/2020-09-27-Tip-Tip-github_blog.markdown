---
layout: post
title:  "[Tip] github 블로그를 만들자!"
subtitle:   "github 블로그를 만들자!"
categories: tip
tags: github git blog
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

[7. github 사용법 - Branch&PR 2편](https://lhmlhm1111.github.io/tip/2020/09/24/Tip-Tip-github_branchPR2/)

[8. github 사용법 - Fork&PR](https://lhmlhm1111.github.io/tip/2020/09/26/Tip-Tip-github_ForkPR/)

---



지난 포스팅까지 `github`를 사용하는 법에 대한 모든 포스팅을 끝마쳤습니다. 보너스로 `github`를 이용해 **블로그**를 구축하는 방법을 포스팅하고 `github`에 대한 글을 마무리 지으려고 합니다. 지난 포스팅 내용들을 잘 따라오셨다면 어렵지 않게 만들 수 있을 것입니다.

먼저 원격 저장소를 만들어 봅시다.

 <img src="https://user-images.githubusercontent.com/47618340/94368777-0850e580-0121-11eb-8f9f-4337416c322b.png" alt="image-20200927183244742" style="zoom:67%;" />

원격 저장소 이름은 `사용자 아이디.github.io`로 지어주셔야 `github`이 자동으로 인식하여 호스팅 해줍니다. 빠르게 결과를 확인해보기 위해 아래쪽에 `Add a README file`을 체크해주시고 `Create repository`를 눌러줍니다. 그리고 해당 원격 저장소를 `clone` 하여 로컬 저장소에 저장해둡시다.

---

바로 결과를 확인해봅시다. 주소창에 아까 입력했던 `사용자 아이디.github.io`를 입력합니다.

![image-20200927184107494](https://user-images.githubusercontent.com/47618340/94368787-19015b80-0121-11eb-97a3-c2e842568967.png)

너무도 간단하게 블로그가 만들어졌습니다. 이제 자기가 원하는 대로 HTML과 CSS를 이용해 커스터마이징 하면 됩니다....만 우리는 공부할 것이 너무 많고 시간은 없어서 블로그 만드는 것에 너무 많은 시간을 쏟을 수는 없습니다. 다행히 수 많은 웹사이트 디자이너들이 다양하고 이쁜 템플릿을 많이 제작해놓으셨습니다. 

---

`github` 블로그는 `Jekyll`이라고 하는 사이트 생성기를 이용해 디자인 할 수 있습니다. [여기](http://jekyllthemes.org/)로 들어오시면 웹 디자이너들이 `Jekyll`을 기반으로 만든 다양한 무료 템플릿이 있습니다. 살펴보시고 원하는 것을 선택하시면 됩니다. `Demo`를 클릭하시면 실제 블로그의 모습을 샘플로 확인할 수 있습니다. 저는 이걸 선택해봤습니다.

![image-20200927233054249](https://user-images.githubusercontent.com/47618340/94368796-274f7780-0121-11eb-8f1f-0601ce680fb6.png)

마음에 드시는 테마를 선택했다면 `Download`를 눌러줍니다. 내려 받은 파일의 압축을 해제하고 폴더 내부의 파일들을 아까 `clone` 해온 로컬 저장소에 저장합니다.

---

`Download` 받은 파일은 처음에 우리가 템플릿을 고를 때 확인했던 `Demo`를 그대로 구현한 것입니다. 샘플을 그대로 쓸 수 없기 때문에 파일 내부의 코드를 수정해서 우리가 원하는 대로 커스터마이징을 해야합니다. 앞에서 말씀드렸던 것처럼 `github`의 테마는 `Jekyll`을 기반으로 개발되었습니다. 때문에 우리도 `Jekyll`을 로컬에 설치해야 코드의 변화에 따라 블로그가 구현되는 모습을 실시간으로 확인할 수 있고 커스터마이징도 가능할 것입니다.

먼저 우리는 `Ruby`라는 언어와 개발 툴킷을 설치해주어야 합니다. `Ruby`를 설치해야 하는 이유는 `Jekyll`이 `Ruby`로 만들어진 프로그램이기 때문입니다. [여기](https://rubyinstaller.org/downloads/)로 들어가 `=>` 표시가 되어있는 버전을 다운 받아 주세요.

![image-20200927221507974](https://user-images.githubusercontent.com/47618340/94368808-39c9b100-0121-11eb-9046-e3aee728da53.png)

---

다운로드가 끝나면 윈도우 검색창에서 `Start Command Prompt with Ruby`를 검색해 실행해줍니다.

<img src="https://user-images.githubusercontent.com/47618340/94368821-4817cd00-0121-11eb-919f-18a422c6ef67.png" alt="image-20200927221916547" style="zoom:50%;" />

---

먼저 위에서 원격 저장소를 Clone 해온 폴더로 이동하고 `chcp 65001`을 실행합니다. 인코딩을 부여하는 명령어로 오류를 줄여주는 역할을 해준다고 합니다.

```ruby
C:\Users\lhmlh>cd lhmlhm1112.github.io
C:\Users\lhmlh\lhmlhm1112.github.io>chcp 65001
```

---

아래의 명령어를 통해 `Jekyll`을 설치해주시면 됩니다.

```ruby
C:\Users\lhmlh\lhmlhm1112.github.io>gem install bundler jekyll minima jekyll-feed tzinfo-data rdiscount
```

---

이제 `Jekyll`의 설치가 끝났습니다. 아래의 코드를 통해 지킬 서버를 구동하고 http://127.0.0.1:4000 로 접속하시면 블로그가 구동되는 모습을 확인할 수 있습니다. 코드를 바꾸면 변화된 모습을 실시간으로 반영하게 됩니다.

```
bundle exec jekyll serve
```

(아마 상기의 과정에서 순탄하게 안되는 분들이 많으실겁니다 ㅠ 각각의 `Jekyll` 템플릿이 각자 다른 버전에서 작성된 것에서 발생하는 문제라고 생각되네요. 웬만한 버전 에러는 터미널 창의 안내를 잘 읽어보시면 해결될 겁니다. 하지만 정말 정말 해결이 안된다면 호환이 잘되는 다른 템플릿을 찾는 것을 추천드려요.)

---

아래와 같이 나타나는 것을 확인할 수 있습니다.

![image-20200928000550358](https://user-images.githubusercontent.com/47618340/94368834-5960d980-0121-11eb-895b-c21c4e57f88f.png)

---

커스터마이징 하는 것은 정말 스스로의 영역입니다. 각각의 템플릿 마다 구조가 달라 일반화하여 설명하기가 어렵습니다. 직접 찾아가며 하나씩 코드를 바꾸면서 수정하시면 됩니다. (저도 완전히 구조를 이해하고 수정하는데 3~4일 소요했습니다ㅠ) 하지만 대부분 `Jekyll` 템플릿이 가지는 일반적인 구조가 있습니다. 가장 참고하기 좋은 것은 [Jekyll 공식 문서](http://jekyllrb-ko.github.io/docs/structure/)입니다. 한글화가 되어 있어 더욱 좋습니다.

반드시 수정해야 하는 파일은 `_config.yml` 입니다. 블로그에 대한 가장 중요한 환경 변수들을 설정하는 파일이므로 본인에 맞게 수정해주시면 됩니다. 포스팅은 `_posts` 폴더에 `.md` 파일을 작성하는 방식으로 할 수 있습니다. 대부분의 템플릿에서 Sample 파일을 넣어두므로 형식을 참고해서 포스팅 하시면 됩니다.

수정이 다 끝났다면 웹에 올리는 일만 남았습니다. 수정된 내역을 원격 저장소에 `push`하면 자동으로 웹에 반영됩니다.

---

이번 포스팅을 끝으로 `git`에 대한 포스팅을 **진짜** 끝마치도록 하겠습니다. 블로그를 만들고 처음으로 올린 시리즈 포스팅이었는데 끝을 내니 정말 뿌듯 뿌듯합니다. 방대한 양을 매일 올리느라 힘들었지만 개인적으로 공부도 많이 돼서 좋았습니다. 이 글을 보신 분들께도 많은 도움이 됐으면 좋겠습니다. 다른 정보 글도 올릴테니 많이 많이 읽어주세요 ㅎㅎ. 혹시나 궁금하신 점이 있다면 댓글로 남겨주시면 확인하는 대로 아는 만큼 답변 드리겠습니다. 읽어주셔서 감사합니다~

