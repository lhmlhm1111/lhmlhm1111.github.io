---
layout: post
title:  "[Tip] github 사용법 - Branch&PR 1편"
subtitle:   "github 사용법 - Branch&PR 1편"
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

[5. github 사용법 - 협업(push&pull)](https://lhmlhm1111.github.io/tip/2020/09/23/Tip-Tip-github_pushpull/) 

---



지난 포스팅에서는 `github`의 협업 시나리오 중 **push & pull**에 대해 알아보았습니다. 이번 포스팅에서는 현재 가장 표준적인 협업 모델인 **Branch & PR**에 대해서 알아보도록 하겠습니다.

끝말 잇기와 같이 간단한 프로젝트의 경우 **push & pull**만으로도 충분하겠지만 복잡한 프로젝트를 수행할 때는 비효율적입니다. 메이플 아일랜드 밖에 없는 메이플 스토리에 빅토리아 아일랜드를 추가한다고 해봅시다. **push & pull** 방식으로 만든다면 개발자`A`가 먼저 리스항구를 만들고 `push`를 하면 개발자 `B`가 그것을 `pull`해서 헤네시스를 만들고 `push`하고 개발자 `C`는 그것을 받아 커닝시티를 만들고... 아마 빅토리아 아일랜드를 만드는데만 10년은 걸릴 것 같습니다. 



그렇다고 각자 만든 것을 본 게임에 `push` 해버리면 에러가 날 것이 자명해보입니다. 심지어는 잘 돌아가고 있던 메이플 아일랜드 마저 망쳐버릴지도 모릅니다. 그렇기 때문에 게임 회사는 본 게임에 반영하기 전에 알파/베타 서버라는 것을 만듭니다. 알파/베타 서버에서 에러가 발생하지 않는지 충분히 실험해보고 수정을 거친 후 본 서버에 반영하게 됩니다. (그럼에도 불구하고 버그가 생긴다는 것이 협업의 어려움을 방증하는 것이기도 합니다 ㅠ)



다시 `git`으로 돌아와봅시다. 예시로 들었던 본 서버를 `git`에서는 **master**, 알파/베타 서버를 **branch**라고 합니다.  그리고 알파/베타 서버의 내용을 본 서버에 반영하는 것을 `merge`라고 합니다. 여기까지는 이해가 잘 됐을 것이라고 생각합니다. 앞으로 설명할 내용은 다소 추상적이므로 시각화를 통해 이해를 돕는 [사이트](https://git-school.github.io/visualizing-git/)를 하나 소개해드리겠습니다. 해당 사이트를 이용해 설명드리도록 하겠습니다.



![image-20200924162902499](https://user-images.githubusercontent.com/47618340/94156087-a1ca8e00-feba-11ea-80c7-9203686f54f7.png)

첫 번째 `commit`이 이루어진 상태를 가정하고 시작합니다. 



## (1) git branch

`git branch`는 브랜치를 생성하는 명령어입니다. `git branch 브랜치이름`으로 생성하시면 됩니다. 저는 `test`라고 이름을 짓도록 하겠습니다.

```shell
$ git branch test
```



![image-20200924163209029](https://user-images.githubusercontent.com/47618340/94156140-b3139a80-feba-11ea-87ea-f0096f127c21.png)



`HEAD` 밑에 `test`라는 브랜치가 생성됐습니다. 아직 브랜치에 아무 것도 `commit`하지 않았기 때문에 가지가 뻗어나가지는 않았습니다.  브랜치에 `commit`을 하기 위해서는 먼저 해당 브랜치를 선택해야 합니다. 이 때 지난 포스트에서 배웠던 `git checkout`을 사용하시면 됩니다. 그리고 `git branch`를 입력하면 현재 존재하는 브랜치와 선택 현황을 알 수 있습니다.

```shell
$ git checkout test
Switched to branch 'test'

$ git branch
  master
* test
```



![image-20200924164156730](https://user-images.githubusercontent.com/47618340/94156183-c161b680-feba-11ea-854e-a946d912246e.png)



`Head`가 `test` 밑으로 이동한 것으로 보아 `test` 브랜치가 선택된 것을 알 수 있습니다. `test` 브랜치에 `commit`해보도록 하겠습니다.

```shell
$ git commit -m "second"
```

![image-20200924164839208](https://user-images.githubusercontent.com/47618340/94156208-ccb4e200-feba-11ea-9080-112639e6f775.png)

`test` 브랜치의 가지가 하나 뻗어나간 것을 볼 수 있습니다. 그럼 이제 `test`를 master 브랜치에 반영하도록 하겠습니다.



## (2) git merge

`git merge`는 두 개의 브랜치를 합치는 명령어 입니다. `git merge 합칠 브랜치 이름`으로 사용하시면 됩니다. 주의하실 점은 **반드시** 메인이 되는 브랜치로 이동해서 사용해야 한다는 것입니다. 만약 master 브랜치에서 `test`를 합친다면 

```shell
$ git checkout master
$ git merge test
```

위의 순서로 하셔야 합니다. 이걸 안 지켜서 피눈물을 흘릴 일이 많을지도...

`git merge`를 사용하는 상황은 3가지로 나눌 수 있습니다.

+ Fast - forward Merge
+ Auto - Merge
+ Conflict



### (2.1) Fast - forward Merge

한 브랜치에만 `commit`이 있다면 적용되는 `merge`입니다.

![image-20200924164839208](https://user-images.githubusercontent.com/47618340/94156208-ccb4e200-feba-11ea-9080-112639e6f775.png)

앞에서 봤던 이 상황에서 Merge를 하면 적용됩니다. 위에서 말했듯이 반드시 master로 `checkout`하고 merge를 하셔야 합니다.

```shell
$ git checkout master
$ git merge test
```

![image-20200924173747840](https://user-images.githubusercontent.com/47618340/94156302-ea824700-feba-11ea-89c3-40cc52c69196.png)

위와 같이 master 브랜치가 `test` 브랜치로 이동하여 `merge`가 이루어집니다.



### (2.2) Auto - Merge

`test` 브랜치 뿐 아니라 `master`에도 `commit`이 생긴 경우를 생각해봅시다. 아래와 같은 상황입니다.

![image-20200924174158524](https://user-images.githubusercontent.com/47618340/94156398-05ed5200-febb-11ea-9db8-a84698dde9a8.png)

다행히 master 브랜치에 새로 `commit`이 일어났음에도 test와 파일 간 충돌이 발생하지 않는다면 **Auto Merge**가 발생하게 됩니다. `merge`를 수행해보도록 하겠습니다.

![image-20200924174407428](https://user-images.githubusercontent.com/47618340/94156484-17365e80-febb-11ea-856b-5f19f4307359.png)

위와 같이 자동으로 `merge`가 수행됩니다.

 

### (2.3) Conflict

가장 골치 아픈 상황입니다.  master 브랜치에 새로 `commit`이 일어나는 과정에서 파일의 수정이 발생해 master 브랜치와 `test` 브랜치 간 충돌이 발생하는 경우입니다. 

![image-20200924174158524](https://user-images.githubusercontent.com/47618340/94156398-05ed5200-febb-11ea-9db8-a84698dde9a8.png)

(2.2)의 상황과 비슷해보이지만 파일 간 충돌이 생겨 자동으로 `merge`가 일어나지 않습니다. `merge`가 가능하도록 직접 파일을 수정해주어야 합니다. 해당 상황을 직접 구현해보겠습니다.

먼저 `a.txt` 파일에 **hi**를 추가하고 `add`, `commit`을 해줍니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ touch a.txt # a.txt 생성

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ echo hi > a.txt # a.txt에 hi 작성

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git add a.txt # add
warning: LF will be replaced by CRLF in a.txt.
The file will have its original line endings in your working directory

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git commit -m "add a.txt" # commit
[master (root-commit) f7a1643] add a.txt
 1 file changed, 1 insertion(+)
 create mode 100644 a.txt
```

---

`test` 브랜치를 생성한 뒤 이동해서 `a.txt` 파일의 내용을 **hi**에서 **hello**로 수정하고 `add`, `commit` 해줍니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git branch test # test 브랜치 생성 

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git checkout test # test 브랜치로 이동
Switched to branch 'test'

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (test)
$ echo hello > a.txt # a.txt 파일을 hi에서 hello로 수정

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (test)
$ git add a.txt # add
warning: LF will be replaced by CRLF in a.txt.
The file will have its original line endings in your working directory

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (test)
$ git commit -m "modify a.txt" # commit
[test 2267a10] modify a.txt
 1 file changed, 1 insertion(+), 1 deletion(-)
```

---

다시 master 브랜치로 이동해 `a.txt` 파일을 **hi my name is hakmin** 으로 수정 후 `add`, `commit` 해줍니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (test)
$ git checkout master # master 브랜치로 이동
Switched to branch 'master'

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ echo hi my name is hakmin > a.txt # a.txt 파일을 hi에서 hi my name is hakmin으로 수정

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git add a.txt # add
warning: LF will be replaced by CRLF in a.txt.
The file will have its original line endings in your working directory

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git commit -m "a.txt modify2" # commit
[master 370117b] a.txt modify2
 1 file changed, 1 insertion(+), 1 deletion(-)
```

`git merge`를 실행한 후 결과를 확인해봅시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git merge test #merge 실행
Auto-merging a.txt
CONFLICT (content): Merge conflict in a.txt
Automatic merge failed; fix conflicts and then commit the result.

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master|MERGING)
$ 
```

**CONFLICT (content): Merge conflict in a.txt** 라는 경고가 뜨면서 경로 옆의 표시가 **(master\|MERGING)**으로 바뀐 것을 확인할 수 있습니다.

---

`git status`를 찍으면 어떤 부분에서 문제가 발생했는지 바로 확인 가능합니다. 

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master|MERGING)
$ git status #상태 확인
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   a.txt
```

**conflict** 상황을 해결하는 방법은 직접 충돌이 난 파일을 수정한 후 `add`, `commit`하는 것입니다. `a.txt` 를 열어보겠습니다.

![image-20200924224834842](https://user-images.githubusercontent.com/47618340/94156646-464cd000-febb-11ea-93e0-6235380bcdee.png)

 신기하게도 충돌이 난 부분이 구분되어 있는 것을 볼 수 있습니다. 아래와 같이 특수 문자를 모두 지운 후 저장하고 `add`, `commit` 해보도록 하겠습니다.

![image-20200924225059184](https://user-images.githubusercontent.com/47618340/94156685-52d12880-febb-11ea-8790-b7f77723ce3f.png)

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master|MERGING)
$ git add a.txt # add

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master|MERGING)
$ git commit -m "merge finish" # commit
[master 9fd2ff1] merge finish

lhmlh@DESKTOP-99JLML6 MINGW64 ~/conflict (master)
$ git status # 상태 확인
On branch master
nothing to commit, working tree clean

```

경로 옆에 표시가 `(master|MERGING)`에서 `(master)`로 변경되었고 `git status`를 찍으면 `commit`이 잘 된 것을 확인할 수 있습니다.

---



쓰다보니 글이 너무 길어져서 **Pull Request**를 보내는 방법에 대해서는 다음 포스팅으로 넘기도록 하겠습니다. 읽어주셔서 감사합니다~

---



### 다음 포스팅

[github 사용법 - branch&PR 2편](https://lhmlhm1111.github.io/tip/2020/09/25/Tip-Tip-github_branchPR2/)