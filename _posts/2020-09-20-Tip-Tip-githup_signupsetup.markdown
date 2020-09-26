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

<img src="https://user-images.githubusercontent.com/47618340/94341959-b9d01800-0048-11eb-9a88-105bf4f6bf23.png" alt="가입화면" style="zoom:50%;" />


녹색 버튼 `Sign up for GitHub`을 클릭하면 가입 화면이 나옵니다.

---



<img src="https://user-images.githubusercontent.com/47618340/94341968-cce2e800-0048-11eb-9d6f-8e094c47442f.png" alt="가입화면2" style="zoom: 67%;" />

정보를 기입하고

---



<img src="https://user-images.githubusercontent.com/47618340/94341976-da986d80-0048-11eb-9eee-96a967880f5b.png" alt="가입화면3" style="zoom:50%;" />



자신이 인간임을 증명한 후 계정을 생성합니다.

---

<img src="https://user-images.githubusercontent.com/47618340/94341993-f69c0f00-0048-11eb-819b-974db8de3a52.png" alt="가입화면4" style="zoom: 67%;" />

위에서 기입한 E-mail로 가서 인증을 하면 가입이 완료됩니다.

---

이제 `git`을 다운로드 받아 봅시다. [여기](https://git-scm.com/)로 들어오세요.

![다운로드](https://user-images.githubusercontent.com/47618340/94342009-16333780-0049-11eb-8bd0-26e0e04e160c.png)

링크로 들어오시면 바로 다운로드 버튼을 볼 수 있습니다. 클릭하시면 자동으로 다운로드 됩니다. 

---



<img src="https://user-images.githubusercontent.com/47618340/94342018-24815380-0049-11eb-809c-00fd5279724f.png" alt="다운로드2" style="zoom: 67%;" />

저는 개인적으로  원래 설정 그대로 다운로드를 받아도 전혀 불편한 점을 못느꼈기 때문에 그대로 쭉 `Next`를 눌러서 `Install` 해주시면 될 것 같습니다. 혹시 세부 설정에 대해 궁금하신 분이 계시다면 [여기](https://goddaehee.tistory.com/216)를 참고해주시면 됩니다.

---



<img src="https://user-images.githubusercontent.com/47618340/94342032-3a8f1400-0049-11eb-9400-9db9b12887ed.png" alt="다운로드3" style="zoom: 67%;" />

설치가 완료됐습니다. `Launch Git Bash`를 체크하고 종료하면 `git bash`가 실행됩니다.

---



<img src="https://user-images.githubusercontent.com/47618340/94342049-4bd82080-0049-11eb-997c-44dd5c2a2b33.png" alt="다운로드4" style="zoom: 67%;" />

이런 화면에 떴다면 제대로 설치가 된 것입니다. 명령창에 `git --version`을 입력하면 버전 정보를 확인할 수 있습니다.

---



<img src="https://user-images.githubusercontent.com/47618340/94342051-4f6ba780-0049-11eb-905c-6a2fe3ecf5f1.png" alt="다운로드5" style="zoom:67%;" />

마지막으로 처음에 가입했던 `github`  계정을 등록시켜주시면 끝이 납니다.

명령창에 `git config --global user.name "사용자"`, `git config --global user.email "사용자 이메일"`을 입력하면 됩니다. 

축하합니다! 이제 `github` 사용할 모든 준비가 끝이 났습니다. 다음 포스팅은 `git bash shell` 에서 사용할 수 있는 기본적인 `Linux` 명령어를 다루도록 하겠습니다. 읽어주셔서 감사합니다~

---

### 다음 포스팅 

[git bash shell 명령어](https://lhmlhm1111.github.io/tip/2020/09/21/Tip-Tip-Shellcommand/)