## 1/14 수업


### [웹 프로그래밍 기술 - 클라이언트]

#### HTML

> Hyper Text Markup Language
>
> 텍스트, 이미지, 동영상 등을 어떻게 표현할지 정하는 언어

* 웹 사이트를 구축하려면 웹 페이지를 먼저 개발해야 한다

* 마크업 방식으로 구현

``` 
<h1> 올라프 </h1>
<h3> 올라프 </h3>

# 하이퍼링크
<a href="http://www.w3schools.com/">올라프</a> 

# 이미지: 종료 태그 없음(싱글사이드 태그)
<img src = "olaf1.png">

# 테이블
<table border="1"><tr><td>올라프</td></tr></table>
# tr: 행
# td: 열
```





#### CSS

> Cascading Style Sheets
>
> HTML 태그에 의해서 웹페이지가 출력(랜더링)될 때 스타일을 조정할 수 있는 기술

```
# 기본 색상: 검정
<h1> 올라프 </h1>

# 색상 변경
<h1 style="color : orange";background-color:green"> 올라프 </h1> 

<style>
	h1{
		color : orange
		background-color:green
	
	}
</style>
```





#### JavaScript

> 웹 페이지를 만들때 프로그램적으로 처리해하는 기능이 있을 때 사용하는 주로 웹 개발에서 사용되는 프로그래밍 언어

* 브라우저에서 수행 가능한 프로그래밍 언어
* 대부분의 브라우저에서는 자바스크립트 인터프리터(엔진)를 내장
* 동적인 웹 페이지 개발 필수 기술



#### URL

> Uniform Resource Locator
>
> 웹 자원의 위치를 알려주는 단일화된 형식의 문자열

* 웹 사이트(웹 페이지) 주소 문자열

* `프로토콜명://서버도메인명(IP주소):포트번호/패스/.../파일명`
  * 프로토콜명: `http(https)://`

* 예시
  * http://localhost:8000
  * http://localhost:8000/edu/first.html
  * http://localhost:8000/edu/htmlexam/exam1.html







### Web Client 기술

#### 웹 표준이란: 어디서든, 누구나 정보를 함께 공유

> W3C에서 정한 표준 기술만 사용
>
> 웹 페이지 작성시 문서의 구조와 표현 방법, 상호 동작을 구분하여 구현
>
> **모든 사용들을 위한 웹 환경 구현**

* HTML: 웹문서 구조 담당



#### HTML5

> * HTML: 문서의 내용과 구조
> * CSS3: 스타일 관련 표현
> * JavaScript: 웹페이지에서의 다양한 동작 구현

* 요소
  * 태그 tag `<>`, `</>`
  * 내용 content `<title> 웹문서내용 </title`>
  * 엘리먼트 element
  * 속성 attribute
  * 속성값 value





* HTML 주소 예제

```
    <title>HTML 학습</title>
</head>
<body>
<h1>주요 HTML 태그 학습</h1>
<hr>
<h2>제목-2</h2>
<h3>제목-3</h3>
<h4>제목-4</h4>
<h5>제목-5</h5>
<h6>제목-6</h6>
<hr>				# 수평선

# 하이퍼링크
<a href="http://www.w3schools.com">W3C School</a>
<a href="http://www.w3.org">W3C</a>
<a href="http://www.python.org">PYTHON</a>

# url
src="http://localhost:8000/edu/images/olaf.jpg">

# 상대 url(같은 서버일 때)
<img src="/edu/images/duke.png">
<img src="../images/r4.gif">

# 사진 크기조절(픽쎌단위)
<img src="../images/r4.gif" width="200" height="100">

# 사진에 이름 쓸 때
	# 제목을 위에
<figure>
<figcaption>올라프</figcaption>
<img src="http://localhost:8000/edu/images/olaf.jpg" width="200" height="100">
</figure>

	# 제목을 아래에
<figure>
<img src="/edu/images/duke.png" width="100" height="500">
<figcaption>듀크</figcaption>
</figure>


# ol: order list (숫자 자동 출력)
<h2>좋아하는 음식</h2>
<ol>
    <li>삼겹살</li>
    <li>떡볶이</li>
    <li>치킨</li>
</ol>

# ul: unorder list (기호 자동 출력)
<h2>좋아하는 색깔</h2>
<ul>
    <li>하늘색</li>
    <li>노란색</li>
    <li>흰색</li>
</ul>

# 4행 2열 테이블 만들기
# <th> 테이블 제목
<table border="1">
    <tr><th>선택자</th><th>기능</th></tr>
    <tr><td>태그선택자</td><td>스타일을 적용할 태그를 찾는다.</td></tr>
    <tr><td>ID선택자</td><td>ID 속성의 값을 가지고 스타일을 적용할 태그를 찾는다.</td></tr>
    <tr><td>CLASS선택자</td><td>CLASS 속성의 값을 가지고 스타일을 적용할 태그를 찾는다.</td></tr>
</table>


# 비디오 추가
<video width="720" height="400" controls>
    <source src="trailer.mp4">
    <source src="trailer.ogg">
</video>
# controls: 동영상 컨트롤러를 내보내는 역할
# mp4 & ogg: 브라우저가 대표적으로 지원하는 동영상 형식

</body>
</html>
```



**www.w3school.com**

**html5test.com**