---
layout: post
title:  "[Tip] git 사용법 - 코드 관리(SCM) & 버전 관리(VCS)"
subtitle:   "git 사용법 - 코드 관리(SCM) & 버전 관리(VCS)"
categories: tip
tags: github git
comments: true
header-img:
---



### 지난 포스팅

[1. 마크다운 문법](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-Markdown/)

[2. github 가입 및 다운로드](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-githup_signup&setup/)

[3. git bash shell 명령어](https://lhmlhm1111.github.io/tip/2020/09/21/Tip-Tip-Shellcommand/)

---



지난 포스팅까지 `git`을 사용하기 위한 빌드업을 했습니다. 이제는 본격적으로 `git`을 사용해보도록 하겠습니다. `git`을 사용하는 용도는 크게 두 가지 입니다.



> 1. 코드 관리(SCM) & 버전 관리(VCS) 도구로서의 `git`
>
> 2. 협업 도구로서의 `git`



기본적으로 `git` 자체는 1번의 기능을 수행하기 위한 것이지만 `github`와 결합되면서 2번의 기능까지 수행할 수 있게 되었습니다. 눈치 채신 분들이 있겠지만 `git`과 `github`는 다릅니다. 둘의 차이에 대해 간단하게 짚고 넘어가도록 하겠습니다.



### git

> **로컬 저장소** (쉽게 말해 자신의 컴퓨터라고 생각하시면 됩니다.) 에서 작업 폴더의 버전을 관리해주는 시스템입니다. 소스 코드의 변경 사항을 버전의 형태로 모두 저장해주어 수정 사항 확인 및 롤백이 쉽습니다.

여담으로 `git`을 개발한 사람은 **Linus Torvalds**라는 사람인데 이름을 보면 아시겠지만 `Linux`를 개발한 사람입니다. 그래서 `git bash`의 명령어는 `Linux`의 명령어를 사용하는 것이고 `Linux` OS에는 `git`이 기본적으로 내장되어 있습니다.



### github

> **원격 저장소** (클라우드와 비슷한 개념입니다.) 에서 작업 폴더의 버전을 관리해주는 시스템입니다. 따라서 작업 폴더에 타인의 접근이 가능해지게 되며 협업 및 배포의 기능을 수행할 수 있게 됩니다.



이번 포스팅에서는 로컬 저장소에서 **코드 관리 및 버전 관리**를 어떻게 하는지에 대해 다룰 것이고 원격 저장소에서 할 수 있는 협업에 관한 내용은 다음 포스팅에서 다루도록 하겠습니다. 먼저 `git bash`를 실행해봅시다. 홈 디렉토리에서 `cd` 명령어를 통해 원하는 디렉토리로 이동해도 되지만 이동하고 싶은 폴더를 열고 마우스 오른쪽을 눌러 `Git Bash Here`를 실행시키면 간단히 이동할 수 있습니다.

<img src="https://user-images.githubusercontent.com/47618340/93906542-46bc5e00-fd37-11ea-923a-a0b0aed0c2c4.png" alt="image-20200922141953898" style="zoom:50%;" />



`git bash`를 열었다면 우리가 작업할 폴더를 만들어주고 이동해봅니다. 저는 작업 폴더의 이름을 `workspace`라고 만들고 이동해보겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ mkdir workspace

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd workspace

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace
$
```



## (1) git init

`git init`은 현재 폴더를 `git` 저장소로 만드는 명령어입니다. 위에서 만든 `workspace`를 `git` 저장소로 만들어보겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace
$ git init
Initialized empty Git repository in C:/Users/lhmlh/workspace/.git/

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
```

눈썰미가 좋은 분이라면 어떤 차이가 생겼는지 바로 눈치채실 수 있을 것입니다. 경로 옆에 `(master)`라는 표시가 붙었습니다. 그리고 해당 폴더를 열어보시면 `.git`이라는 폴더가 생긴 것을 확인할 수 있습니다. 이제 `workspace` 폴더는 `git`에서 버전 관리를 해주는 폴더가 되었습니다. 만약 더이상 해당 폴더를 `git`에서 관리하고 싶지 않다면 `.git` 폴더를 지워주시면 됩니다.



## (2) git status

`git status`는 `git`의 관리 현황을 출력해줍니다. 한 번 입력해봅시다.

```shell
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

한 줄 씩 읽어보면

---

> On branch master

현재 master라는 branch에 있다. (branch의 개념은 다음 포스팅에서 설명하겠습니다.)

> No commits yet

아직 아무것도 commit 된 것이 없다.

> nothing to commit (create/copy files and use "git add" to track)

commit 할 것이 없다. 파일을 만들어서 `git add` 해달라.

---

출력된 텍스트를 미루어 볼 때 `git`에서 작업물을 관리하기 위해서는 먼저 파일을 만들고 그것을  `add`하고 `commit`을 해야하는 구나라고 생각해볼 수 있습니다. `workspace`에 `touch` 명령어를 이용해 `a.txt` 파일을 생성해보고 다시 `git status`를 입력해보겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ touch a.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        a.txt

nothing added to commit but untracked files present (use "git add" to track)
```

뭔가 다른 텍스트가 출력됐습니다. 

> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
>         a.txt
>
> nothing added to commit but untracked files present (use "git add" to track)

'`git`에게 추적되지 않은 파일이 발견되었다. `commit`을 하고 싶다면 `git add`를 사용해서 추적할 수 있게 해라.' 

대략 이런 말인 것 같습니다. 이제 가장 중요한 `git add`와 `git commit`에 대해 알아봅시다.

## (3) git add & git commit

`git`의 작동 방식을 흔히 사진을 찍는 것에 비유합니다. 각자 폰을 들고 사진기 어플을 실행해봅시다. 사진을 찍기 위해서는 먼저 찍고자 하는 대상을 렌즈에 비춰야합니다. 이것이 `git`에서 파일을 `add`하는 것과 같습니다.  `a.txt`를 `add`를 통해 렌즈에 비춰봅시다. `git add 파일명` 형식으로 입력하시면 됩니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git add a.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt
```

> Changes to be committed:
>   (use "git rm --cached <file>..." to unstage)
>         new file:   a.txt

새로운 파일 `a.txt`가 `git`에게 인식된 것을 확인할 수 있습니다.

---

사물을 렌즈에 올리기만 하면 사진은 찍히지 않습니다. 셔터를 눌러야 비로소 사진이 찍히고 앨범에 저장이 되는 것이죠. 셔터를 눌러 앨범에 저장하는 것이 `git`에서는 `commit`한다고 말합니다. 셔터를 눌러봅시다. `git commit -m "해당 버전에 대한 설명"` 으로 입력하시면 됩니다. "해당 버전에 대한 설명"을 쓰는 이유는 해당 버전의 기능, 수정내역 등 대해 한 눈에 파악하기 위해서 입니다. 사진으로 비유하면 사진을 저장할 때 사진을 찍은 날짜와 장소 등으로 이름을 붙여줘야 하는 것과 동일합니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git commit -m "add a.txt"
[master (root-commit) 907b729] add a.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git status
On branch master
nothing to commit, working tree clean
```

---

축하합니다! `git` 저장소에 첫 번째 버전을 올리는데 성공했습니다. 여세를 몰아 두 번째 세 번째 버전도 올려보도록 하겠습니다. `b.txt`와 `c.txt`파일을 차례대로 `add`, `commit` 해봅시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ touch b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git add b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git commit -m "add b.txt"
[master 2a61a16] add b.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ touch c.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git add c.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git commit -m "add c.txt"
[master d3a48c7] add c.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 c.txt
```

`workspace`에는 세 가지 버전이 생겼습니다. 버전 정보를 확인해보도록 하겠습니다.



## (4) git log

`git log`는 현재까지의 버전 정보를 모두 출력하는 명령어 입니다. 좀 더 깔끔한 출력을 위해 두 가지 옵션이 있습니다.



> + `git log --oneline`  : 버전 정보를 한 줄로 출력합니다.
> + `git log --숫자` : 특정 개수만 출력합니다.



`git log --oneline` 명령어를 통해 버전 정보를 출력해봅시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git log --oneline
d3a48c7 (HEAD -> master) add c.txt
2a61a16 add b.txt
907b729 add a.txt
```

`d3a48c7`, `2a61a16`, `907b729`은 각 버전의 일련 번호입니다. 일련 번호와 함께 `commit`할 때 함께 썼던 설명이 출력됩니다. `git`은 이런 식으로 작업 폴더의 변경 이력을 모두 저장합니다. 

---

앗! 그런데 갑자기 `c.txt` 파일에 치명적인 오류가 발생하였습니다. 도저히 수정이 불가능한 오류이기 때문에 `c.txt` 파일을 만들기 이전의 버전으로 돌아가고 싶습니다. 어떻게 하면 좋을까요?



## (5) git checkout

`git checkout`은 특정 시점의 버전을 체크할 수 있는 명령어 입니다. `git checkout 해당 버전의 일련번호`를 입력합니다. `c.txt`를 추가하기 전 버전으로 돌아가 봅시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git checkout 2a61a16
Note: switching to '2a61a16'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 2a61a16 add b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace ((2a61a16...))
$ ls
a.txt  b.txt
```

`ls` 명령어를 입력하니 놀랍게도 `c.txt`가 사라진 것을 확인할 수 있습니다. 해당 파일을 열고 들어가면 `c.txt`가 사라진 것을 알 수 있습니다. 하지만 이것은 실제로 과거의 버전으로 돌아간 것이 아니라 과거의 버전을 조회한 것에 불과합니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)

HEAD is now at 2a61a16 add b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace ((2a61a16...))
```

위의 코드에서 중요한 텍스트 세 줄만 가져왔습니다. 눈치 채셨겠지만 경로 옆에 붙은 표시가 처음에는 `master` 였다가  '`HEAD`가 `2a61a16`에 있습니다.' 라는 말 다음에 `2a61a16`로 바뀌었습니다. `git` 세상에서 현재의 기준은 항상 `master`입니다. `git checkout`은 타임머신과 같아서 과거로 이동할 수는 있지만 엄연히 현재는 `master`에 존재합니다. 즉 `git checkout`을 통해 과거를 현실로 만든 것이 아니라 현실은 그대로 두고 과거로 이동했을 뿐이라는 것입니다. 그렇다면 현재를 아예 없던 일로 만들고 과거를 다시 현재로 만들어 버리는 방법은 있을까요? 물론 있습니다.



## (6) git reset

`git reset`은 현재를 아예 없던 일로 만들고 과거를 다시 현재로 만들어 버리는 명령어 입니다. 현재를 없애버리기 위해서는 우선 현재로 다시 돌아가야 합니다. `git checkout master`를 입력하여 현재로 돌아갑시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace ((2a61a16...))
$ git checkout master
Previous HEAD position was 2a61a16 add b.txt
Switched to branch 'master'

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ ls
a.txt  b.txt  c.txt
```

`git reset`을 통해 `c.txt`가 없었던 버전으로 돌아가 보겠습니다.  `git reset 돌아가고 싶은 버전의 일련번호` 로 입력해주시면 됩니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git log --oneline
d3a48c7 (HEAD -> master) add c.txt
2a61a16 add b.txt
907b729 add a.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git reset 2a61a16

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git log --oneline
2a61a16 (HEAD -> master) add b.txt
907b729 add a.txt
```

`git checkout`을 했던 때와 다르게 이번엔 경로 옆에 그대로 `master`가 유지됐습니다. `git log`를 통해 변경 이력을 확인해보면 `c.txt`를 추가했던 이력이 사라졌습니다. 여기서 주의해야할 것은 `git`에서 `reset`을 한 것이 작업 폴더에 반영되지는 않는다는 것입니다. 다만 `git`에 `commit`되기 이전으로 돌아간 것 뿐입니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ ls
a.txt  b.txt  c.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/workspace (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        c.txt

nothing added to commit but untracked files present (use "git add" to track)
```

`ls`를 입력하면 `c.txt`는 그대로 있습니다. 하지만 `git status`를 입력하면 `c.txt`가 `git`에 `commit`되지 않았다는 것을 알 수 있습니다.



지금까지 `git`을 이용하여 로컬 저장소에서 코드 관리 및 버전 관리를 하는 방법에 대해서 알아봤습니다. 다음 포스팅에서는 `github`를 이용해 협업하는 방법을 다뤄보도록 하겠습니다. 읽어주셔서 감사합니다~



### 다음 포스팅

[github 사용법 - 협업(push&pull)](https://lhmlhm1111.github.io/tip/2020/09/23/Tip-Tip-github_push&pull/)







