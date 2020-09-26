---
layout: post
title:  "[Tip] github 사용법 - Branch&PR 2편"
subtitle:   "github 사용법 - Branch&PR 2편"
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

---



지난 포스팅에서는 `github`의 협업 시나리오 중 하나인 **Branch & PR** 모델에서 브랜치를 생성하고 `merge`를 수행하는 방법을 알아봤습니다. 이번 포스팅에서는 **PR (Pull request)**을 하는 방법에 대해 알아보겠습니다. 

**PR**이란 말 그대로 **브랜치**가 **master**에게 자신의 작업물을 `pull` 해줄 것을 요청(request)하는 것입니다. 협업 상황에서 **브랜치**가 **PR**을 거치지 않고 마음대로 자신의 작업물을 master에 `push` 한다면 버그를 관리하는 것이 굉장히 어려울 것입니다. master는 **PR**을 통해 브랜치의 작업물을 신중하게 검토해볼 수 있고 다른 브랜치의 작업물과 비교하는 것을 통해 더 나은 것을 선택할 수도 있을 것입니다.

**PR** 상황을 직접 구현해보려면 계정이 두 개가 필요합니다. 같이 공부하는 친구가 있다면 친구와 함께 따라해보시면 될 것 같습니다. 만약 저처럼 친구가 없다면 (또륵...) 계정을 하나 더 만드신 다음 해보셔도 좋습니다.

먼저 원격 저장소를 만든 다음 Collaborator를 초대하는 방법을 보여드리도록 하겠습니다. 원격 저장소를 만들고 로컬 저장소와 연결시키는 방법은 생략하겠습니다. [지난 포스트](https://lhmlhm1111.github.io/tip/2020/09/23/Tip-Tip-github_push&pull/)를 참고해주세요.

---

<img src="https://user-images.githubusercontent.com/71595415/94272964-c25c1c00-ff7e-11ea-9838-920904ba530c.png" alt="image-20200925205010351" style="zoom:50%;" />

원격 저장소를 생성한 다음 Settings를 클릭해주세요.

---

<img src="https://user-images.githubusercontent.com/71595415/94272994-cf790b00-ff7e-11ea-8888-2205334078b1.png" alt="image-20200925205232524" style="zoom:50%;" />

좌측 중단에 있는 Manage access를 클릭합니다.

---

<img src="https://user-images.githubusercontent.com/71595415/94273068-e3247180-ff7e-11ea-9634-1f9f52237bfe.png" alt="image-20200925205415645" style="zoom:50%;" />

살짝 아래로 내리면 Invite a collaborator를 볼 수 있습니다. 클릭해주세요.

---

<img src="https://user-images.githubusercontent.com/71595415/94273114-efa8ca00-ff7e-11ea-9e46-ed6da3ad7fd7.png" alt="image-20200925205643670" style="zoom:50%;" />

초대하길 원하는 사용자의 아이디를 입력하고 Add to this repository 버튼을 클릭하면 초대가 완료됩니다.

---

이제 초대를 받은 사람의 입장입니다. 초대를 받기 위해서는 가입할 때 입력한 이메일로 들어가줍니다.

<img src="https://user-images.githubusercontent.com/71595415/94273165-00594000-ff7f-11ea-8185-4de3096d3e61.png" alt="image-20200925211343620" style="zoom:50%;" />

View invitation을 누르면 초대 페이지로 이동합니다. 

---

<img src="https://user-images.githubusercontent.com/71595415/94273235-18c95a80-ff7f-11ea-8f6d-2e7c1f702eb5.png" alt="image-20200925211717192" style="zoom:50%;" />

Accept invitation을 누르시면 수락됩니다.

---

이제 두 명의 collaborator가 하나의 원격 저장소에서 협업을 하게 되었습니다! 프로젝트의 주제는 **3행시 짓기** 입니다. 원격 저장소를 만든 사람이 프로젝트의 팀장, 초대를 받은 사람이 팀원이라고 합시다. 협업의 흐름은 다음과 같습니다.



1. 팀장은 **README.md**를 통해 3행시 과제를 내줍니다.
2. 팀원은 3행시를 완성시키고 팀장에게 **PR**을 보냅니다.
3. 팀장은 팀원이 보낸 **PR**의 내용을 확인하고 마음에 들면 master 브랜치에 `merge` 합니다.



---

먼저 팀장이 되어보도록 하겠습니다. 삼행시 과제 파일을 만들고 파일 이름을 **README.md**로 짓습니다. `github`는 **README.md**라는 이름의 파일을 자동으로 인식해 원격 저장소에 대한 소개 글로 나타냅니다.

<img src="https://user-images.githubusercontent.com/71595415/94273336-3c8ca080-ff7f-11ea-84c5-00a6f702a379.png" alt="image-20200925213258929" style="zoom:50%;" />

`typora`를 이용해 위와 같이 3행시 과제 파일을 만들고 `add`, `commit`, `push` 해줍니다. 반드시 **README.md**라는 이름으로 만들어야 소개글로 나타나게 됩니다.

---

<img src="https://user-images.githubusercontent.com/71595415/94273387-4f9f7080-ff7f-11ea-8589-80d6f2585257.png" alt="image-20200925213657527"  />

원격 저장소에 이렇게 나오면 제대로 된 것입니다.

---

이제 팀원이 되어봅시다. 먼저 `git pull`을 통해 원격 저장소를 로컬로 가져온 다음 **반드시** 브랜치를 생성해줍니다. 브랜치를 생성하지 않고 바로 master로 `push` 해버리는 순간 아마 팀장님이 죽이러 오실지도 모릅니다...ㅎ (물론 실제로는 master branch로 push 할 수 있는 권한 자체가 주어지지 않을 것입니다.)

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git pull origin master
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 270 bytes | 18.00 KiB/s, done.
From https://github.com/lhmlhm1111/collabo
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git branch hakmin

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git checkout hakmin
Switched to branch 'hakmin'

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (hakmin)
$
```

위와 같이 먼저 branch를 생성하고 이동한 후 삼행시를 수정해줍니다.

<img src="https://user-images.githubusercontent.com/71595415/94273488-73fb4d00-ff7f-11ea-86fc-dbe597afcd31.png" alt="image-20200925215235768" style="zoom:67%;" />

---

늘 하듯이 `add`, `commit`을 하고 **절대로** `git push origin ` **master**를 해서는 안됩니다. 계속 강조하지만 **master** 브랜치에 바로 push하는 것은 아무런 검증도 하지 않고 본 서버에 업데이트를 해버리는 것입니다. 따라서 원격 저장소에 브랜치를 생성하고 그곳에 `push`를 해야합니다. `git push origin 브랜치이름`으로 해주시면 됩니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (hakmin)
$ git add README.md

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (hakmin)
$ git commit -m "modify README.md"
[hakmin 8dd21c7] modify README.md
 1 file changed, 3 insertions(+), 3 deletions(-)

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (hakmin)
$ git push origin hakmin #절대 master로 push하면 안됨
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 375 bytes | 187.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'hakmin' on GitHub by visiting:
remote:      https://github.com/lhmlhm1111/collabo/pull/new/hakmin
remote:
To https://github.com/lhmlhm1111/collabo.git
 * [new branch]      hakmin -> hakmin
```

---

그럼 이제 다시 원격 저장소로 가보도록 합시다. 아무 변화가 없는 것 같지만 사실 변화가 생겼습니다. 

![image-20200925220340381](https://user-images.githubusercontent.com/71595415/94273686-b02ead80-ff7f-11ea-9fd9-a16eb4ee2441.png)

빨간색으로 표시한 부분을 클릭하면

---

![image-20200925220439798](https://user-images.githubusercontent.com/71595415/94273730-c177ba00-ff7f-11ea-926e-8c79aed8c255.png)

`hakmin` 이라는 브랜치가 생긴 것을 발견할 수 있습니다. 클릭해주세요.

---

<img src="https://user-images.githubusercontent.com/71595415/94273844-e9ffb400-ff7f-11ea-99e1-7dae1c91f547.png" alt="image-20200925220727319" style="zoom:50%;" />

`hakmin` 브랜치에 수정된 사항이 반영된 것을 볼 수 있습니다. 우측 상단에 `Pull request`를 클릭해줍니다.

---

![image-20200925221027919](https://user-images.githubusercontent.com/71595415/94273896-f97efd00-ff7f-11ea-9124-b9a88b005211.png)

이제 팀장님께 채택해달라고 싹싹 비시면 됩니다. Create pull request를 눌러줍니다.

---

![image-20200925221628376](https://user-images.githubusercontent.com/71595415/94273967-0f8cbd80-ff80-11ea-8c85-f641f880610a.png)

모든 **PR**의 목록은 좌측 상단의 Pull request 탭에서 확인 가능합니다. 만약 삼행시가 마음에 들면 중간에 있는 Merge pull request를 누른 후 Confirm merge를 눌러주시면 됩니다. 만약 마음에 들지 않는다면 Close pull request를 눌러 기각시키면 됩니다. Merge를 하고 master 브랜치로 이동해봅시다.

(참고로 Merge를 하고 나면 브랜치를 지울 것인지 물어봅니다. 대부분의 경우 branch는 일회용이므로 그때 그때 지워주는 것이 좋다고 합니다.)

---

![image-20200925222152137](https://user-images.githubusercontent.com/71595415/94274018-229f8d80-ff80-11ea-8a13-e6172a2a8bff.png)

제대로 merge가 된 것을 확인할 수 있습니다. 

---



지금까지 **Branch & PR** 모델에 대해 알아보는 시간을 가졌습니다. **Branch & PR**은 매우 효율적인 협업 모델이지만 Collaborator로 초대되지 않은 사람은 협업에 참여할 수 없다는 한계가 있습니다. 이러한 한계점을 보완하기 위한 협업 모델이 다음 포스트에서 다룰 **Fork & PR** 모델이 되겠습니다. 읽어주셔서 감사합니다~

---

### 다음 포스팅

[github 사용법 - Fork & PR](https://lhmlhm1111.github.io/tip/2020/09/26/Tip-Tip-github_ForkPR/)

