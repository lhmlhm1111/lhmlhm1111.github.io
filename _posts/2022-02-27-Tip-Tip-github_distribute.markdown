---
layout: post
title:  "[Tip] github page에 문서 배포하기"
subtitle:   "github page에 문서 배포하기"
categories: tip
tags: git github markdown
comments: true
header-img:
---



### 지난 포스팅

[github 블로그를 만들자!](https://lhmlhm1111.github.io/tip/2020/09/27/Tip-Tip-github_blog/)

---



오랜만에 포스팅합니다. 이번 포스팅에서는 지난 번에 만들었던 `github` 블로그의 URL을 이용해  `Rmarkdown` 문서를 배포해보도록 하겠습니다. `github` 블로그를 먼저 개설해야 page에 배포하는 것이 가능하므로 이전 포스팅을 먼저 보시고 오시기 바랍니다. 

먼저 다음과 같이 원격 저장소를 만들어 봅시다.

<img src="https://user-images.githubusercontent.com/47618340/155866425-257d15b1-be72-4722-b4c2-6a72ef5f8ba0.png" alt="image-20220227115556920" style="zoom: 67%;" />



원격 저장소가 만들어졌다면 `Settings` 탭을 클릭합니다. 

![image-20220227120000249](https://user-images.githubusercontent.com/47618340/155866436-12f40b69-3234-45a5-a053-774807036620.png)



좌측 메뉴에서 `pages` 탭을 클릭합니다.

![image-20220227120544149](/home/hakmin/.config/Typora/typora-user-images/image-20220227120544149.png)

`Source` 메뉴의 `None` 탭에서 `main`을 선택합니다.

![image-20220227121159729](/home/hakmin/.config/Typora/typora-user-images/image-20220227121159729.png)

다음으로 `/(root)`를 `/docs`로 바꿔주고 `Save`를 클릭합니다.

![image-20220227121449313](/home/hakmin/.config/Typora/typora-user-images/image-20220227121449313.png)



이제 방금 만든 원격저장소의 `docs` 폴더 내에 있는 파일들은 웹으로 배포됩니다. 미리 만들어놓은 `Rmarkdown` 문서를 `docs` 폴더에 넣고 원격저장소에 push 하겠습니다.

![image-20220227123754358](/home/hakmin/.config/Typora/typora-user-images/image-20220227123754358.png)



이제 잘 배포가 되었는지 확인해봅시다. 주소는 `블로그주소/원격저장소이름/문서이름.html`로 들어가시면 됩니다. 

![image-20220227124252590](/home/hakmin/.config/Typora/typora-user-images/image-20220227124252590.png)

위의 문서를 직접 확인해보고 싶다면 [여기](https://lhmlhm1111.github.io/distribute_test/Rmarkdown_practice.html)로 들어가보시면 됩니다. 읽어주셔서 감사합니다~
