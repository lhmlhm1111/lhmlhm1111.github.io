---
layout: post
title:  "[Tip] github 가입 및 다운로드"
subtitle:   "github 가입 및 다운로드"
categories: tip
tags: github
comments: true
header-img:
---



### 지난 포스팅

[1. 마크다운 문법](https://lhmlhm1111.github.io/tip/2020/09/20/Tip-Tip-Markdown/)

---



지난 포스트에서는 `Markdown` 문법에 대해 알아보았습니다. 원래는 `Linux shell` 명령어를 다음 포스팅으로 할려고 했는데 생각해보니 우선 `git bash`을 다운 받아야 직접 써볼 수 있기 때문에 `github` 가입 및 다운을 이번 포스팅의 주제로 잡게 되었습니다. 먼저 [깃허브 홈페이지](https://github.com/)로 들어갑니다. 

![로그인화면](https://user-images.githubusercontent.com/47618340/93713545-a4b23f80-fb97-11ea-99ce-4fad75d503a1.png)


녹색 버튼 `Sign up for GitHub`을 클릭하면 가입 화면이 나옵니다.

---



![image-20200920221037545](https://user-images.githubusercontent.com/47618340/93713583-d9be9200-fb97-11ea-9248-c58a7f4a6777.png)

정보를 기입하고

---



![image-20200920221126595](https://user-images.githubusercontent.com/47618340/93713606-fc50ab00-fb97-11ea-90b8-bb76ccff501a.png)



자신이 인간임을 증명한 후 계정을 생성합니다.

---



![image-20200920221631017](https://user-images.githubusercontent.com/47618340/93713672-4b96db80-fb98-11ea-8bea-65200503f352.png)

위에서 기입한 E-mail로 가서 인증을 하면 가입이 완료됩니다.

---



이제 `git`을 다운로드 받아 봅시다. [여기](https://git-scm.com/)로 들어오세요.

![image-20200920223209536](https://user-images.githubusercontent.com/47618340/93713674-4fc2f900-fb98-11ea-852e-620db9fe5e62.png)

링크로 들어오시면 바로 다운로드 버튼을 볼 수 있습니다. 클릭하시면 자동으로 다운로드 됩니다. 

---



![image-20200920223838756](https://user-images.githubusercontent.com/47618340/93713678-56517080-fb98-11ea-8aa9-571215f476b8.png)

저는 개인적으로  원래 설정 그대로 다운로드를 받아도 전혀 불편한 점을 못느꼈기 때문에 그대로 쭉 `Next`를 눌러서 `Install` 해주시면 될 것 같습니다. 혹시 세부 설정에 대해 궁금하신 분이 계시다면 [여기](https://goddaehee.tistory.com/216)를 참고해주시면 됩니다.

---



![image-20200920224715760](https://user-images.githubusercontent.com/47618340/93713680-59e4f780-fb98-11ea-850c-35ade8885960.png)

설치가 완료됐습니다. `Launch Git Bash`를 체크하고 종료하면 `git bash`가 실행됩니다.

---



![image-20200920225130198](https://user-images.githubusercontent.com/47618340/93713682-5cdfe800-fb98-11ea-907c-7cee097349ae.png)

이런 화면에 떴다면 제대로 설치가 된 것입니다. 명령창에 `git --version`을 입력하면 버전 정보를 확인할 수 있습니다.

---



![image-20200920230409100](https://user-images.githubusercontent.com/47618340/93713685-5ea9ab80-fb98-11ea-9f83-8f492dd9d472.png)

마지막으로 처음에 가입했던 `github`  계정을 등록시켜주시면 끝이 납니다.

명령창에 `git config --global user.name "사용자"`, `git config --global user.email "사용자 이메일"`을 입력하면 됩니다. 

축하합니다! 이제 `github` 사용할 모든 준비가 끝이 났습니다. 다음 포스팅은 `git bash shell` 에서 사용할 수 있는 기본적인 `Linux` 명령어를 다루도록 하겠습니다. 읽어주셔서 감사합니다~



### 다음 포스팅 

[git bash shell 명령어](https://lhmlhm1111.github.io/tip/2020/09/21/Tip-Tip-Shellcommand/)