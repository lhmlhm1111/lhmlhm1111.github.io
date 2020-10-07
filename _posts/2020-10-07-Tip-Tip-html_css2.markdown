---
layout: post
title:  "[Tip] 웹크롤링을 위한 HTML과 CSS 2편"
subtitle:   "웹크롤링을 위한 HTML과 CSS 2편"
categories: tip
tags: webcrawling html css
comments: true
header-img:
---



### 지난 포스팅

[1. 웹크롤링을 위한 HTML과 CSS 1편](https://lhmlhm1111.github.io/tip/2020/10/07/Tip-Tip-html_css1/)

---



지난 포스팅에서는 `HTML`의 구조와 자주 쓰는 태그에 대해서 알아봤습니다. 이번 포스팅에서는 `CSS`에 대해서 알아보도록 하겠습니다. 지난 번에 간단히 설명했듯이 `CSS`는 홈페이지를 꾸미는데 사용되는 언어입니다. 웹 크롤링이 목적인 우리가 왜 `CSS`에 대해 알아야 할까요? 바로 **선택자**(Selector)라는 개념 때문에 그렇습니다.

길게 말할 것 없이 바로 예시로 넘어가겠습니다. 지난 포스팅에서 소개해드렸던 `Visaul Studio Code`를 이용해 `HTML` 파일과 `CSS` 파일을 하나씩 생성해보도록 하겠습니다.



![image-20201007213440990](https://user-images.githubusercontent.com/47618340/95346529-eca2c780-08f6-11eb-947f-e3792c2510b7.png)

표시한 파일 생성 버튼을 눌러 아래와 같이 생성해줍니다. 메모장을 열고 확장자명을 `.html`, `.css`로 저장해도 동일하게 생성됩니다.

---

생성했다면 `HTML` 파일을 아래와 같이 작성해줍니다. `<link rel="stylesheet" href="test.css">` 코드를 `<head>` 부분에 작성해주면 `css` 파일과 연결됩니다. 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="test.css"> <!--css 파일과 연결해주는 코드입니다.-->
    <title>Document</title>
</head>
<body>
	<h1>CSS 연습!!</h1> <!--제목-->
    
    <div> <!--구역을 나눠주는 태그-->
        <ul> <!--순서가 없는 목록-->
            <li>빨강</li>
            <li>파랑</li>
        </ul>
    </div>

    <span> <!--구역을 나눠주는 태그-->
        <ol> <!--순서가 있는 목록-->
            <li>노랑</li>
            <li>초록</li>
        </ol>
    </span>
    
</body>
</html>
```

저장 후 `HTML` 파일을 실행해봅니다. 잘 작성했다면 아래와 같이 나올 것입니다.

![image-20201007215916597](https://user-images.githubusercontent.com/47618340/95346559-f5939900-08f6-11eb-9c7b-1408ab6fb54b.png)

---

이제 `CSS`를 이용하여 `HTML` 문서를 꾸며보도록 하겠습니다. 이번 포스팅에서 할 것은 글자에 색을 입히는 것입니다. 먼저 몸풀기로 **CSS 연습!!** 이라는 제목을 보라색으로 색칠해보겠습니다. `CSS`는 텍스트에 접근할 때 기본적으로 `HTML`의 태그를 이용합니다. `CSS` 파일을 열고 아래와 같이 작성하고 저장한 다음 html 파일을 열어주세요.

```css
h1 {
    color: purple;
}
```

![image-20201007223504001](https://user-images.githubusercontent.com/47618340/95346574-fa584d00-08f6-11eb-8f3d-869fe70e21d2.png)

**태그**인 `h1`을 입력하여 위처럼 제목 텍스트 **CSS 연습!!**에 접근해 보라색으로 바꾸었습니다. 

---

같은 방식으로 `li` 태그를 이용해 목록 텍스트에도 접근할 수 있을 것입니다. 아래와 같이 입력해주고 확인해봅시다.

```css
li {
    color: red;
}
```

![image-20201007224129312](https://user-images.githubusercontent.com/47618340/95346625-06dca580-08f7-11eb-982b-f780016d815f.png)

문제가 생겼습니다! 우리는 각각의 목록 텍스트에 다른 색깔을 칠하고 싶은데 모든 `li` 태그에 일괄적으로 빨간색이 적용되어 버렸습니다. 이때 우리는 **선택자**라는 유용한 도구를 사용합니다. 말 그대로 각각의 요소를 "선택" 하기 위한 코드를 의미합니다.

`HTML` 코드로 돌아와봅시다. 코드를 찬찬히 살펴보면 `li`이 모두 같은 `li`이 아니라는 것을 알 수 있습니다. 위의 두 `li`은 **부모 요소**가 `ul`이고 아래의 두 `li`은 **부모 요소**가 `ol`인 점을 확인할 수 있습니다.

```html
<div> <!--구역을 나눠주는 태그-->
    <ul> <!--순서가 없는 목록-->
        <li>빨강</li>
        <li>파랑</li>
    </ul>
</div>

<span> <!--구역을 나눠주는 태그-->
    <ol> <!--순서가 있는 목록-->
        <li>노랑</li>
        <li>초록</li>
    </ol>
</span>
```

---

부모 요소의 차이를 이용해 위쪽의 `li`은 빨간색, 아래쪽 `li`는 노란색을 칠해봅시다. 부모 요소를 구분해줄 때는 `>`를 **선택자**로 사용합니다.

```css
ul > li {
    color: red;
}

ol > li {
    color: yellow
}
```

![image-20201007225458330](https://user-images.githubusercontent.com/47618340/95346649-0b08c300-08f7-11eb-9eb6-7fbbeb673abd.png)

---

부모 요소를 통해 위, 아래의 목록 텍스트를 구분하는데 성공했습니다! 하지만 여전히 만족스럽지 않습니다. 우리의 목표는 모든 목록 텍스트에 서로 다른 색을 칠하는 것입니다. 하지만 더 이상 부모 요소를 통해 구분해줄 여지는 없어보입니다. 이 때 우리는 각각의 목록을 `HTML`의 **속성**값을 이용해 구분해줄 수 있습니다. 지난 포스팅에서 `class`와 `id` 속성에 대해 잠깐 언급했습니다. 두 가지 속성을 통해 각각의 목록을 구분해주도록 하겠습니다. `HTML`코드를 아래와 같이 수정해줍니다.

```html
<div>
    <ul>
        <li id="red">빨강</li>
        <li id="blue">파랑</li>
    </ul>
</div>

<span>
    <ol> 
        <li class="yellow">노랑</li>
        <li class="green">초록</li>
    </ol>
</span>
```

---

`id`와 `class`는 각각의 요소에 고유한 이름을 붙이는 **속성**라고 생각하시면 됩니다. 둘은 거의 유사하지만 **선택자**에 차이가 있습니다. `id`는  `#`을 **선택자**로, `class`는 `.`을 선택자로 사용합니다. `CSS` 코드를 아래와 같이 수정한 후 결과를 확인합니다.

```css
li#red {
    color: red;
}

li#blue {
    color: blue;
}

li.yellow {
    color: yellow;
}

li.green {
    color: green;
}
```

![image-20201007232211309](https://user-images.githubusercontent.com/47618340/95346665-0fcd7700-08f7-11eb-9e44-a14f33b55b2b.png)

드디어 각각의 목록을 구분하여 색칠하는데 성공했습니다!

---

우리는 이번 포스팅에서 `CSS`의 선택자를 통해 텍스트를 선별하고 각자 다른 처리를 했습니다. 이것은 우리가 웹크롤링을 하는 행위와 일맥상통합니다. 웹 상에 있는 수 많은 데이터 중 우리에게 필요한 것만 가져오기 위해서는 위에서 사용했던 **부모요소**와 **속성**을 통해 데이터를 구분해내고 **선택자**를 통해 선별해야 합니다. 다음 포스팅에서 다루겠지만 우리는 `python` 모듈인 `BeautifulSoup`을 이용합니다. `BeautifulSoup`으로 데이터를 가져올 때 `CSS` 선택자를 사용하게 될 것입니다.

다음 포스팅에서는 본격적으로 `python`의 `requests` 모듈을 이용한 웹크롤링을 다루도록 하겠습니다. 읽어주셔서 감사합니다~