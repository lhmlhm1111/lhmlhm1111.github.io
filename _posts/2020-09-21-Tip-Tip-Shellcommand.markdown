---
layout: post
title:  "[Tip] git bash shell 명령어"
subtitle:   "git bash shell 명령어"
categories: tip
tags: github shell
comments: true
header-img:
---



### 지난 포스팅

[1. 마크다운 문법](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-Markdown/)

[2. github 가입 및 다운로드](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-githup_signupsetup/)

---



지난 포스팅에서 우리는 간단한 `Markdown` 문법을 알아봤고 `github` 가입 및 설치까지 완료했습니다. 이번 포스팅에서는 `git bash shell`에서 사용할 수 있는 기본적인 `Linux` 명령어를 알아보도록 합시다. `git`을 직접 다루는 명령어는 따로 다룰 예정입니다. 이번에는 디렉토리 및 파일의 조회, 이동, 생성, 삭제 같은 기본적인 명령어에 대해 다루도록 하겠습니다.

먼저 `git bash`를 실행해봅시다. 윈도우 검색창에 `git bash`를 검색하면 바로 나옵니다.

![image-20200921133654247](https://user-images.githubusercontent.com/47618340/93740356-43d14880-fc25-11ea-9b37-cb7d6e861faf.png) 

가장 먼저 우리는 `git bash`가 어디에서 실행되고 있는지를 알아야 합니다. 명령창 제목부분에서 `git bash`가 실행된 디렉토리의 경로를 확인할 수 있습니다. 저의 경우에는 `c/Users/lhmlh` 이 되겠네요. 

그리고 바로 아래를 보시면 노란색 `~`을 확인할 수 있습니다. 이것은 **홈 디렉토리**를 의미합니다. `git bash` 상에서의 경로 이동은 모두 **홈 디렉토리**에서 부터 시작됩니다. 저의 현재 경로가 `c/Users/lhmlh`이고 명령창에는 `~` 밖에 나와있지 않으니 즉 `c/Users/lhmlh`이 **홈 디렉토리**라는 의미입니다. 



## 1. pwd

현재 디렉토리의 경로를 확인하는 명령어 입니다.

```shell
$ pwd
/c/Users/lhmlh

```

현재는 어떤 디렉토리로도 이동하지 않았으니 홈 디렉토리의 경로가 그대로 출력됩니다.



## 2. ls

현재 디렉토리 내부에 존재하는 폴더와 파일의 목록을 호출하는 명령어 입니다. (아이에스 아니고 엘에스입니다.)

```shell
$ ls
'3D Objects'/
 4IR/
 anaconda3/
 AppData/
'Application Data'@
 Contacts/
 Cookies@
 Desktop/
.
.
.
```

폴더의 경우 파란색으로 호출되는 것을 볼 수 있습니다. 저는 `4IR` 폴더로 이동해보도록 하겠습니다.

## 3. cd

현재 디렉토리에서 다른 디렉토리로 이동하는 명령어 입니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd 4IR

lhmlh@DESKTOP-99JLML6 MINGW64 ~/4IR
```

---



명령어를 입력했더니 `~` 에서 `~/4IR`로 바뀐 것을 확인할 수 있습니다. 이 상태에서 `ls` 명령어를 입력해봅시다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/4IR
$ ls
__pycache__/     employees2.xml  MySQL.ipynb  test6.py        수행평가제출.zip
AI/              employees3.xml  staff.py     test7.py        클래스.ipynb
Algorithm.ipynb  emps.txt        test.py      test8.py        회원관리.ipynb
API.ipynb        gugudan.py      Test2.py     tkinter.ipynb
calc.py          Hello.py        Test3.py     tkinter2.ipynb
calculator.py    mod2.py         test4.py     xml.ipynb
employees.xml    MyApp/          test5.py     노트북.ipynb
```

이전과는 다른 목록이 호출되는 것을 확인할 수 있습니다.

---



상위 디렉토리로 돌아가기 위해서는 `cd ..`을 입력해주시면 됩니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/4IR
$ cd ..

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$

```

---



당연히 한 칸 씩만 이동할 수 있는 것은 아닙니다. `cd 해당 폴더의 절대 경로`  혹은 `cd 해당 폴더의 상대 경로` 를 입력해 주시면 한 번에 멀리 있는 폴더로 이동하는 것이 가능합니다. 

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd ./DSL/EDA_Project/housesalesprediction

lhmlh@DESKTOP-99JLML6 MINGW64 ~/DSL/EDA_Project/housesalesprediction
$ pwd
/c/Users/lhmlh/DSL/EDA_Project/housesalesprediction
```

위에서 배운 `pwd`를 입력하면 한 번에 멀리 있는 폴더로 이동했다는 것을 확인할 수 있습니다.

---



다시 홈 디렉토리로 돌아오고 싶다면 `cd ~` 를 입력하시면 됩니다.

```
lhmlh@DESKTOP-99JLML6 MINGW64 ~/DSL/EDA_Project/housesalesprediction
$ cd ~

lhmlh@DESKTOP-99JLML6 MINGW64 ~
$
```

 한 방에 집으로 돌아올 수 있습니다.



## 4. mkdir

현재 위치에 폴더를 생성하는 명령어 입니다. 비교를 위해 빈 폴더로 이동해서 보여드리겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~
$ cd emptyfolder

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ ls

```

---



`emptyfolder` 폴더에는 아무 것도 없기 때문에 `ls` 명령어를 입력했을 때 아무 것도 나오지 않습니다. `mkdir` 명령어를 이용해 폴더를 생성해보겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ mkdir newfolder

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ ls
newfolder/
```

`mkdir` 명령어로 `newfolder`라는 새로운 폴더를 생성하고 `ls`를 입력하니 목록에 등장하는 것을 확인할 수 있습니다. 

주의하실 점은 폴더/파일 이름을 지을 때 `git bash`가 띄어쓰기를 잘 인지하지 못하므로 띄어쓰기를 넣고 싶다면 가급적 `_`를 이용하시는 것이 좋습니다.



## 5. touch

현재 폴더에 파일을 생성하는 명령어 입니다. 기존에 만들었던 `emptyfolder`에 파일을 생성해보도록 하겠습니다. 

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ touch a.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ ls
a.txt  newfolder/

```

`a.txt` 파일이 생성된 것을 확인할 수 있습니다. 파일을 생성할 때 확장자를 반드시 붙여주셔야 합니다



## 6. mv

파일을 이동시킬 때 사용하는 명령어 입니다. `mv 파일 경로`의 형태로 입력하시면 됩니다. 방금 생성한 `a.txt` 파일을 `newfolder`로 이동시켜 보겠습니다.

 ```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ mv a.txt newfolder

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ ls
newfolder/
 ```

`ls`로 확인해보니 `a.txt` 파일이 사라진 것을 확인할 수 있습니다. `newfolder`로 이동해서 확인해보겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ cd newfolder

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ ls
a.txt
```

`newfolder`로 `a.txt`가 이동한 것을 확인할 수 있습니다. 

---

여담으로 `mv` 명령어는 파일의 이름을 바꾸는데도 사용할 수 있습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ mv a.txt b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ ls
b.txt
```

`a.txt` 파일이 `b.txt`로 바뀐 것을 확인할 수 있습니다.



## 7. echo & cat

`echo`는 입력된 값을 그대로 출력해주는 명령어 입니다. 파이썬의 `print` 같은 명령어라고 보시면 됩니다.

```shell
$ echo Hello world
Hello world
```

우리는 `echo 문자열 > 파일` 명령어를 이용해서 파일에 문자열을 입력하는 것이 가능합니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ echo Hello world > b.txt
```

실제로 `Hello world` 가 `b.txt` 파일에 입력되었는지 확인해보려면 직접 해당 경로에 들어가 b.txt 파일을 열어보시면 됩니다. 하지만 `cat` 명령어를 사용하면 명령창에서도 확인이 가능합니다. `cat`은 파일의 내용을 출력해주는 명령어 입니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ cat b.txt
Hello world
```

`echo 문자열 > 파일` 명령어는 기존 파일의 문자열을 모두 지우고 새로 입력을 하게 됩니다. 만약 기존 문자열을 유지하고 새로운 문자열을 추가하고 싶다면 `echo 새로운 문자열 >> 파일`를 사용하시면 됩니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ echo Hello world >> b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ cat b.txt
Hello world
Hello world
```



## 8. rm

`rm`은 파일이나 폴더를 삭제하는 명령어 입니다. 파일을 삭제할 때는 `rm` 명령어를 그대로 사용하면 되지만 폴더를 삭제할 때는 `rm -r`이라는 옵션을 사용해야 합니다. 먼저 파일부터 삭제해보겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ rm b.txt

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ ls
```

`ls`를 통해 확인해보니 아무것도 남아있지 않은 것을 확인할 수 있습니다. 이번엔 폴더를 삭제해보도록 하겠습니다.

```shell
lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder/newfolder
$ cd ..

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ rm -r newfolder

lhmlh@DESKTOP-99JLML6 MINGW64 ~/emptyfolder
$ ls
```

역시 `newfolder`가 사라진 것을 확인해볼 수 있습니다.



물론 `Linux` 명령어는 이것보다 훨씬 많지만 적어도 `github`를 이용하는데 있어서는 이정도만 숙지해도 이용하는 것에 전혀 지장이 없습니다. 다음 포스팅에서는 본격적으로 `git`에 대한 내용을 다룰 예정입니다. 읽어주셔서 감사합니다~

---

### 다음 포스팅

[git 사용법 - 코드관리(SCM) & 버전 관리(VCS)](https://lhmlhm1111.github.io/tip/2020/09/22/Tip-Tip-git/)

