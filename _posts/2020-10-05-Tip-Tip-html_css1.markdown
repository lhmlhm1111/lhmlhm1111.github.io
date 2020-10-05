---
layout: post
title:  "[Tip] 웹크롤링을 위한 HTML과 CSS 1편"
subtitle:   "웹크롤링을 위한 HTML과 CSS 1편"
categories: tip
tags: webcrawling html css
comments: true
header-img:
---



`github`에 대한 포스팅을 마무리 짓고 이번에는 `python`을 활용한 웹크롤링을 주제로 글을 써보려고 합니다. **웹크롤링** (Web Crawling)이란 웹(Web)에서 데이터를 가져오는 행위를 통칭하는 말입니다. 본격적으로 웹크롤링을 다루기에 앞서 웹페이지를 구성하는 언어인 `HTML`과 `CSS`에 대해 간단한 빌드업을 하고 넘어가려고 합니다. 

`HTML`과 `CSS`에 대해 간략하게 설명을 드리면

### HTML (Hyper Text Mark-up Language)

> 웹 페이지의 모습을 나타내기 위한 **마크업 언어**의 일종



### CSS (Cascading Style Sheet)

> HTML의 디자인적인 요소를 표현하는 언어



간단히 말해 `HTML`은 홈페이지의 내용과 구조를 담당하는 언어이고 `CSS`는 글꼴, 색상 등 스타일을 담당하는 언어입니다. 실제로 어떻게 쓰이는지 알아봅시다. `Chrome`을 통해 네이버에 접속 후 우상단 점 세 개 버튼을 클릭하고 `도구 더보기 > 개발자 도구`를 클릭합니다.

<img src="https://user-images.githubusercontent.com/47618340/95106897-1f708280-0774-11eb-8b5a-fd54a86517e4.png" alt="image-20201005221547681" style="zoom:50%;" />

---

클릭하면 아래와 같은 화면을 볼 수 있습니다. 상단에는 `HTML`, 하단에는 `CSS`라고 적혀있는 것을 확인할 수 있습니다. 아래와 같은 마크업 언어를 통해 홈페이지가 구현되는 것입니다. 

<img src="https://user-images.githubusercontent.com/47618340/95106913-24353680-0774-11eb-87c1-7eac66a38872.png" alt="image-20201005221852984" style="zoom:50%;" />

`HTML`과 `CSS`는 웹 개발자 특히 프론트 엔드 개발자라면 반드시 알아야 하는 웹의 근간이 되는 언어입니다. 당연히 제대로 공부하려면 굉장히 방대하고 어렵지만 우리의 목적은 웹을 만드는 것이 아니라 이미 만들어진 웹사이트에서 필요한 정보만을 가져오는 것이므로 매우 기본적인 구조와 자주 쓰이는 태그 및 선택자에 대해서만 다루도록 하겠습니다. 원활한 이해를 돕기 위해 직접 `HTML`과 `CSS` 문서를 작성하면서 설명하겠습니다. 저는 `Visual Studio Code`라는 텍스트 편집기를 이용하여 작성할 것입니다. [여기](https://code.visualstudio.com/)서 다운 받을 수 있습니다. `Visual Studio Code`를 사용하여 따라오는 것을 추천하지만 다운 및 환경 설정에 어려움을 느끼시는 분들은 기본 메모장에 코드를 작성하시고 `.html`, `.css`를 확장자로 하여 저장 후 실행하시면 똑같이 구현됩니다.

---

`Visual Studio Code`의 환경 구성 및 `HTML` 파일 생성은 [여기](https://m.blog.naver.com/PostView.nhn?blogId=mathesis_time&logNo=221610656211&targetKeyword=&targetRecommendationCode=1)를 참고해주세요. `HTML` 파일을 생성했다면 `!` 를 입력 후 `Enter`를 눌러주시면 아래와 같은 코드가 자동 생성되는 것을 확인할 수 있습니다.

```html
<!DOCTYPE html> <!--HTML 문서임을 선언-->
<html lang="en"> 
<head> <!--웹사이트에 대한 설명 부분-->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body> <!--웹사이트의 내용을 표시하는 부분-->
    
</body>
</html>
```

이것이 `HTML`의 가장 기본적인 구조입니다. `<head>`와 `</head>` 사이에는 웹사이트의 제목과 설명이 들어가는 부분이고 `<body>`와 `<\body>` 사이에는 웹사이트의 내용이 들어가는 부분입니다. 둘 다 아주 중요한 부분이지만 웹 크롤링이 목적인 우리는 내용 부분인 `body`에 주목하면 됩니다. 

`body`에 내용을 채워넣어보도록 합시다. `HTML`을 작성하는 방법은 **태그**와 **속성**을 사용하는 것입니다. 기본적인 구조는 아래와 같습니다.

```html
<태그 속성="색상" 속성="글꼴">쓰고 싶은 내용</태그>
```

위에서 봤던 `<head></head>`, `<body></body>`도 모두 **태그**입니다. `<태그>`를 여는 태그, `</태그>`를 닫는 태그라고 합니다. 여는 태그와 닫는 태그 사이에 쓰고 싶은 내용을 넣으면 `HTML` 문서가 작성됩니다. 태그 내부에 **속성**을 넣어주면 글자색, 폰트 등을 변경할 수 있고 태그 간에 구분을 지어 줄 수도 있습니다. 백문이 불여일견 직접 작성해봅시다.



## (1) \<h1>, \<h2>, ..., \<h6>

제목(Header)을 작성하는 태그입니다. 아래와 같이 작성 후 저장하고 파일을 열어봅니다.

```html
<!DOCTYPE html> <!--HTML 문서임을 선언-->
<html lang="en"> 
<head> <!--웹사이트에 대한 설명 부분-->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body> <!--웹사이트의 내용을 표시하는 부분-->
	<h1>Hello HTML!</h1>
	<h2>Hello HTML!</h2>
	<h3>Hello HTML!</h3>
	<h4>Hello HTML!</h4>
	<h5>Hello HTML!</h5>
	<h6>Hello HTML!</h6>
</body>
</html>
```

![image-20201005231854092](https://user-images.githubusercontent.com/47618340/95106920-27c8bd80-0774-11eb-920d-a2592b7831f0.png)

위와 같이 작성된 것을 확인할 수 있습니다. 1에서 6으로 갈수록 소제목이 되는 것을 확인할 수 있습니다. 

여기서 중요한 개념 하나를 짚고 넘어가겠습니다. `<h1>`~`<h6>` 태그는 `<body>` 태그의 하위 항목으로 작성됐다는 것을 발견하실 수 있습니다. 이 때 상위 태그인 `<body>`를 **부모태그**, 하위 태그인 `<h1>` ~ `<h6>`를 **자식태그**라고 부릅니다. 이후에도 많이 등장하는 개념이므로 꼭 알고 넘어가도록 합시다.

---

이번엔 **속성**을 이용해 `<h1>` 태그의 문자열만 빨간색으로 바꿔보도록 하겠습니다. 재차 말씀드리지만 우리의 목적인 웹사이트를 만드는 것이 아니라 웹의 구조를 아는 것입니다. 대략 저런 식으로 **속성**을 부여할 수 있구나를 알고 넘어가시면 됩니다.

```html
<!DOCTYPE html> #HTML 문서임을 선언
<html lang="en"> 
<head> <!--웹사이트에 대한 설명 부분-->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body> <!--웹사이트의 내용을 표시하는 부분-->
	<h1 style="color: red;">Hello HTML!</h1> <!--h1 태그 문자열에 속성 부여-->
	<h2>Hello HTML!</h2>
	<h3>Hello HTML!</h3>
	<h4>Hello HTML!</h4>
	<h5>Hello HTML!</h5>
	<h6>Hello HTML!</h6>
</body>
</html>
```

![image-20201005233602596](https://user-images.githubusercontent.com/47618340/95106930-2a2b1780-0774-11eb-82bc-c9818560c6ad.png)

위와 같이 색상 **속성**이 `<h1>` 태그의 문자열에 부여된 것을 알 수 있습니다. 색상 외에도 수 없이 많은 속성값들이 존재합니다. 특히 웹 크롤링에서 가장 많이 보게 될 속성은 `id`와 `class`입니다. 두 속성에 대해서는 `CSS`를 다룰 때 자세히 설명하도록 하겠습니다.



## (2) \<p>, \<br> ,\<a>

`<p>`는 문단을 나눠주는 태그, `<br>`은 줄바꿈 태그 입니다. `<br>` 태그처럼 닫는 태그가 없이 독립적으로 사용되는 경우도 있다는 것을 알아두시면 좋을 것 같습니다.

`<a>`는 문자열에 링크를 걸어주는 태그로 `href` 속성에 URL를 부여하는 방식으로 사용됩니다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h2>자기 소개</h2>

    <p> <!--문단 태그-->
        안녕하세요 저는 핵민리라고 합니다. <br> <!--줄바꿈 태그-->
        용인에 살고 있고 롤하는거 좋아합니다. <br>
        제 블로그 많이 많이 봐주세요 ㅎㅎ
    </p>
    
    <p>
        우리 집에는 똘이라는 백구가 살고 있습니다. <br> 
        남들에겐 까칠하지만 내 주인한텐 따뜻한 차도견이죠. <br>
        <!--링크 태그-->
        똘이 사진도 <a href="https://lhmlhm1111.github.io/">블로그</a>에 종종 올릴게요~
        
    </p>

</body>
</html>
```

![image-20201006003937903](https://user-images.githubusercontent.com/47618340/95106942-2eefcb80-0774-11eb-9871-917103daa395.png)

## (3) \<ul>, \<ol>, \<li>

목록 관련 태그로 `<ul>`은 순서가 없는 목록을, `<ol>`은 순서가 있는 목록을 표시합니다. `<li>`는 `<ul>` 혹은 `<ol>`의 자식 태그로서 각 항목을 나타냅니다. 웹 크롤링 시 정말 많이 보게 될 태그들입니다. 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p> 
       <ul>
           <li>순서가 없는 항목</li>
           <li>순서가 없는 항목</li>
       </ul> 
    </p>
    
    <p>
        <ol>
            <li>순서가 있는 항목</li>
            <li>순서가 있는 항목</li>
        </ol>
    </p>

</body>
</html>
```

![image-20201006005614565](https://user-images.githubusercontent.com/47618340/95106951-344d1600-0774-11eb-9b74-db408054112b.png)

## (4) \<div>, \<span>

웹 사이트 내의 공간 배치를 위해 사용하는 태그입니다. 웹 사이트 디자인에서는 아주 중요한 태그이며 확실히 구분할 필요가 있지만 웹 크롤링의 입장에서 둘의 차이를 구분하는 것은 별로 중요하지 않습니다. 다만 `div`와 `span` 단위로 우리가 수집하고자 하는 데이터가 구분되어 있다는 사실만 알고 있으면 됩니다. 그래도 궁금하신 분들은 아래의 예시를 보면 어느 정도 이해하실 수 있습니다. 자세한 설명은 생략하겠습니다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div style="background: red;">
        첫번째 div
    </div>

    <div style="background: yellow;">
        두번째 div
    </div>

    <span style="background: lime;" style="">첫번째 span</span>
    <span style="background: blueviolet;">두번째 span</span>
</body>
</html>
```

![image-20201006011727401](https://user-images.githubusercontent.com/47618340/95106963-37e09d00-0774-11eb-9833-9e502d38aad5.png)

---

위에서 계속 언급했지만 웹크롤링이 목적이라면 HTML에 대해 더 자세하게 공부할 필요는 없습니다. 본 포스팅에서 정리한 내용만 훑어봐도 충분합니다. 혹시 더 궁금하신 분은 [w3school](https://www.w3schools.com/html/)을 추천드립니다. 

다음 포스팅은 `CSS`와 선택자에 대해 다룰 것입니다. 다음 포스팅이 웹 크롤링에 있어 좀 더 중요한 내용이라고 생각합니다. 차차 알게 되겠지만 `CSS`가 `HTML`에 스타일링을 하는 방식이 `python` 패키지가 웹의 데이터를 선택하고 가져오는 방식과 거의 유사하기 때문입니다. 다음 포스팅에서 자세히 다루도록 하겠습니다. 읽어주셔서 감사합니다~