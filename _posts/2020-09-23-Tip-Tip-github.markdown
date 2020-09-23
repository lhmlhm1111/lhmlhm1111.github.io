---
layout: post
title:  "[Tip] github 사용법 - 협업(push-pull)"
subtitle:   "github 사용법 - 협업(push-pull)"
categories: tip
tags: github git
comments: true
header-img:
---



### 지난 포스팅

[1. 마크다운 문법](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-Markdown/)

[2. github 가입 및 다운로드](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-githup_signup&setup/)

[3. git bash shell 명령어](https://lhmlhm1111.github.io/tip/2020/09/21/Tip-Tip-Shellcommand/)

[4. git 사용법 - 코드 관리(SCM) & 버전 관리(VCS)](https://lhmlhm1111.github.io/tip/2020/09/22/Tip-Tip-git/)

---



지난 포스팅에서는 로컬 저장소의 코드 관리 및 버전 관리를 위한 `git` 사용법을 알아봤습니다. 이번 포스팅에서는 `github`에서 제공하는 원격 저장소를 통해 다른 사람과 **협업**을 하는 방법을 알아보고자 합니다. `github`에서 할 수 있는 협업의 시나리오는 크게 3가지로 나눌 수 있습니다.



+ ### push & pull

+ ### Branch & PR (Pull Request)

+ ### Fork & PR



이번 포스팅에서는 우선 가장 간단한 협업 시나리오인 **push & pull**에 대해 알아보도록 하겠습니다. 원활한 이해를 돕기 위해 상황을 하나 가정해보도록 하겠습니다. 



> 나는 현재 직장에 다니고 있다. 근데 일이 너무 많아서 주말에도 집에서 잔업을 해야하는 상황이다. 회사에서 하던 작업을 그대로 집에 가져와서 하고 싶은데 어떻게 하면 좋을까? 



협업이라고 보기 애매할수도 있지만 멀리 떨어진 두 개의 작업 폴더를 함께 이용해 작업한다는 점에서 협업의 한 가지 형태라고도 볼 수 있을 것입니다. 이런 상황에서 `github`를 사용하지 않는 사람들도 다양한 형태의 원격 저장소를 사용합니다. 예를 들면 이메일, 카톡, 구글 클라우드 등이 있습니다. 지난 포스팅에서 말했던 것처럼 `git`은 다른 저장소에 비해 변경 사항을 관리하기가 쉽다는 장점이 있어 훨씬 편하게 작업을 이어나갈 수 있습니다.



가장 먼저 해야 하는 것은 `github`에 원격 저장소를 생성하는 것입니다. `github` 홈페이지에 접속하여 로그인 해줍니다.

![image-20200923091957360](2020-09-23-Tip-Tip-github.assets/image-20200923091957360.png)

좌측 상단에 보시면 `Repositories`라는 메뉴가 보일 것입니다. `Repository`는 원격 저장소와 같은 말입니다. 줄여서 `repo`라고도 부릅니다. 새로운 `repo`를 만들기 위해 `New` 버튼을 눌러줍니다.

---

<img src="2020-09-23-Tip-Tip-github.assets/image-20200923093130761.png" alt="image-20200923093130761" style="zoom:50%;" />

`new`를 누르면 위와 같은 화면이 나옵니다. 적절한 이름을 설정하고 `Create repository`를 눌러주세요. 저는 `test`라고 짓도록 하겠습니다.

---

<img src="2020-09-23-Tip-Tip-github.assets/image-20200923095301560.png" alt="image-20200923095301560" style="zoom:50%;" />

위와 같은 화면이 나오면 원격 저장소가 잘 만들어진 것입니다. 이제 만들어진 원격 저장소를 로컬 저장소와 연결시킬 것입니다. 위 화면에 빨간 색으로 표시된 주소 부분을 복사하시고 `git bash`를 열어주세요. 



## (1) git remote

`git remote`는 원격 저장소를 관리하는 명령어 입니다. 먼저 `git remote add` 명령어를 통해 새로운 원격 저장소를 로컬에 연결할 것입니다. 먼저 지난 포스팅에서 배운대로 연결할 폴더를 만들고 `git init`으로 `git` 저장소를 만들어 줍니다. 저는 `house`라는 폴더와 `company`라는 폴더를 만들고 각각을 `git`저장소로 하여 집과 회사에서 번갈아 가며 작업하는 상황을 가정해보도록 하겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ mkdir house

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd house

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house
$ git init
Initialized empty Git repository in C:/Users/lhmlh/house/.git/

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ cd ..

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ mkdir company

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd company

lhmlh@DESKTOP-99JLML6 MINGW64 ~/company
$ git init
Initialized empty Git repository in C:/Users/lhmlh/company/.git/
```

한 가지 주의하실 점은 이미 `git init`을 실행한 폴더의 하위 폴더에는 `git init`을 실행해서는 안됩니다. 이것은 마치 대한민국에도 대통령이 있고 충청도에 또 대통령이 있는 상황과 같습니다. 이런 상황에서는 당연히 명령의 충돌이 생겨 에러가 발생하게 됩니다.

---

로컬 저장소와 원격 저장소를 연결하는 명령어는 `git remote add 원격저장소이름 원격저장소주소` 입니다. 원격 저장소의 이름은 자신이 원하는 대로 지어도 상관 없지만 첫 번째(원본) 원격 저장소의 이름은 `origin`으로 짓는 것이 관례입니다. 두 폴더를 원격 저장소에 연결해봅시다. `git remote` 명령어로 현재 원격 저장소 연결 현황을 조회할 수 있습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git remote add origin https://github.com/lhmlhm1111/test.git

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git remote
origin

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ cd ..

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd company

lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ git remote add origin https://github.com/lhmlhm1111/test.git

lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ git remote
origin
```

두 폴더 모두 `git remote`의 결과로 `origin`이 출력된 것을 확인했습니다.



## (2) git push

`git push`은 로컬 저장소의 작업을 원격 저장소에 저장시키는 명령어 입니다. 회사에서 당신에게 시킨 일은 끝말 잇기 입니다. `wordchain.txt`를 `company` 폴더에 저장해봅시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ touch wordchain.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ echo 깃허브 쿵쿵따! > wordchain.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ cat wordchain.txt
깃허브 쿵쿵따!
```

 하루 종일 열심히 일했지만 일을 다 끝내지 못한 당신은 `wordchain.txt` 파일을 원격 저장소에 저장하고 이후에 집에서 작업을 하려고 합니다. 원격 저장소에 저장하기 위해서는 먼저 `wordchain.txt` 파일을 `git`에 `add`, `commit` 해주어야 합니다. 

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ git add wordchain.txt
warning: LF will be replaced by CRLF in wordchain.txt.
The file will have its original line endings in your working directory

lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ git commit -m "끝말잇기 해주세요 룰은 쿵쿵따입니다 한방단어 자제해주세요"
[master (root-commit) cc6893b] ?앸쭚?뉕린 ?댁＜?몄슂 猷곗? 荑듭영?곗엯?덈떎 ?쒕갑?⑥뼱 ?먯젣?댁＜?몄슂
 1 file changed, 1 insertion(+)
 create mode 100644 wordchain.txt
```

그 다음 `git push 원격저장소이름 branch이름` 을 입력하시면 원격 저장소로 저장이 됩니다. 원격 저장소 이름은 origin으로 지었고 현재 branch는 master 입니다. 즉 `git push origin master`를 입력해주시면 됩니다.  

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ git push origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 305 bytes | 152.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/lhmlhm1111/test.git
 * [new branch]      master -> master
```

제대로 `push`가 되었는지 확인하기 위해 `github`에 만든 원격 저장소로 들어갑니다.

![image-20200923133738937](2020-09-23-Tip-Tip-github.assets/image-20200923133738937.png)

위와 같이 됐다면 제대로 저장이 된 것입니다.



## (3) git pull

일을 미처 다 끝내지 못한 당신은 남은 일을 집에서 하려고 합니다. 남은 일을 하기 위해서 원격 저장소에 저장해 둔 작업 파일을 가져와야 합니다. 이때 사용하는 명령어가 `git pull`입니다. `push`할 때와 동일하게 `git pull 원격저장소이름 branch이름`으로 입력하면 됩니다. 아까 만들어 둔 `house` 폴더로 이동하고 원격 저장소에서 작업 폴더를 가져옵시다. 원격 저장소 이름과 branch 이름도 모두 동일하므로 `git pull origin master`를 입력해주시면 됩니다. 

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/company (master)
$ cd ..

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd house

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git pull origin master
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 285 bytes | 13.00 KiB/s, done.
From https://github.com/lhmlhm1111/test
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master
 
lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ ls
wordchain.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ cat wordchain.txt
깃허브 쿵쿵따!
```

잘 가져와진 것을 확인할 수 있습니다. 다시 동일한 방식으로 집에서 작업한 뒤 원격 저장소에 저장시켜 봅시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ echo 브라질 쿵쿵따! >> wordchain.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ cat wordchain.txt
깃허브 쿵쿵따!
브라질 쿵쿵따!

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   wordchain.txt
```

작업을 마치고 `git status`를 찍으면 

> modified:   wordchain.txt

똑똑한 `git`은 변경사항을 귀신 같이 체크해줍니다. `add`, `commit` 후 `push`해줍시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git add wordchain.txt
warning: LF will be replaced by CRLF in wordchain.txt.
The file will have its original line endings in your working directory

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git commit -m "브라질 쿵쿵따! 추가"
[master dde204a] 釉뚮씪吏?荑듭영?? 異붽?
 1 file changed, 1 insertion(+)

lhmlh@DESKTOP-99JLML6 MINGW64 ~/house (master)
$ git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 302 bytes | 151.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/lhmlhm1111/test.git
   cc6893b..dde204a  master -> master
```

다시 원격 저장소를 확인해보시면

![image-20200923140130922](2020-09-23-Tip-Tip-github.assets/image-20200923140130922.png)

잘 된 것을 확인할 수 있습니다.



## (4) git clone

`git clone` 명령어를 통해 좀 더 쉽게 원격 저장소의 작업 폴더를 가져올 수 있습니다. `git clone 원격저장소 주소`를 입력하시면 됩니다. 원격 저장소의 주소는 원격 저장소 오른쪽에 초록색으로 된 `code` 버튼을 누르면 확인할 수 있습니다.

당신은 갑작스럽게 외국으로 출장을 떠나게 됐습니다. 전에 하던 끝말잇기를 끝마치지 못해서 해외에서도 작업을 해야하는데 깜박하고 노트북을 안가져왔습니다. 그래서 원격 저장소에 저장된 작업 폴더를 현지 컴퓨터로 가져오려고 합니다. 

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ mkdir USA

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd USA

lhmlh@DESKTOP-99JLML6 MINGW64 ~/USA
$ git clone https://github.com/lhmlhm1111/test.git
Cloning into 'test'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), 555 bytes | 20.00 KiB/s, done.

lhmlh@DESKTOP-99JLML6 MINGW64 ~/USA
$ ls
test/
```

`USA` 폴더에 `test` 폴더가 그대로 복제된 것을 확인할 수 있습니다. 말 그대로 복제한 것이기 때문에 따로 `git init`과 `git remote add`를 해줄 필요가 없이 바로 `git` 저장소로 사용할 수 있다는 점에서 편합니다.

---



이번 포스트에서는 `github`의 협업 방법 중 하나인 **push & pull** 방식에 대해 알아봤습니다. 가장 간단하고 직관적인 방식이지만 동시에 여러 작업을 수행하는 것에는 한계점이 있습니다. 주로 끝말 잇기처럼 앞의 task가 끝나야 뒤의 task가 시작될 수 있는 협업에 사용됩니다.  

다음 포스트에서는 현재 개발 업계에서 가장 표준적인 협업 모델인 **Branch & PR (Pull Request)** 방식과 오픈소스 협업 모델인 **Fork & PR** 방식에 대해 알아보도록 하겠습니다. 읽어주셔서 감사합니다~

