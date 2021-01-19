## 1/18 수업(1)

### [웹 클라이언트]_1/24까지 평가

#### 테이블 출력

```
<table>
<tr><th>제목1</th><th>제목2</th><th>제목3</th></tr>
<tr><td>내용1</td><td>내용2</td><td>내용3</td></tr>
</table>
```

* 테이블 스타일

```
# 표 테두리 지정
<style>
	table, th, td {
		border : 1px solid black;
		border-collapse : collapse;			<!--표테두리 한줄로-->
	}

# 제목칸 배경색 지정
	th {
		background-color : lime;
	}
</style>
```

```
# 표 꾸미기
td {
		border-bottom : 1px dotted black;	<!-- 내용행들 바닥줄 점선표시-->
	}
th {
		background-color : lime;
	}
tr:hover {
		background-color : pink;			<!--마우스를 올렸을 때 색 지정-->
	}
th:nth-of-type(1) {
		width : 100px;						<!-- 첫번째 행 사이즈-->
	}
th:nth-of-type(2) {
		width : 400px;
	}
```



#### web form

* `<input>`에 추가된 요소들
  * `<input type="email">`: 이메일 주소 입력시 사용, 서버로 전송시 이메일 형식 자동체크
  * `<input type="url">`: 웹사이트 주소 입력시 사용
  * `<input type="number">`: 스핀 박스를 이용하여 입력가능
  * `<input type="range">`: 슬라이드 막대를 숫자 선택
  * `<input type="search">`: 검색 상자 삽입
  * `<input type="date/month/week/time">`: 달력에서 날짜 선택하거나 스핀박스에서 시간 선택
  * `<input type="color">`: 색상 선택 상자 표시
* `required`: 서버로 폼을 전송하기 전에 필수 필드에 내용이 모두 채워졌는지 검사





#### html 문서의 구조

* 기존 레이아웃 방식: `<div>`
* 시맨틱 레이아웃 방식: 문서의 의미구조를 명확하고 간결하게 표현
  * `<header>`: 주로 머리말, 제목
  * `<nav>`: 주로 메뉴에 사용, 위치 영향X, 사이트간에 서로 연결하는 링크 역할 담당 
  * `<section>`: 본문
  * `<article>`: 실질적인 내용
  * `<aside>`: 본문 외의 내용, 광고나 링크
  * `<footer>`: 화면의 구조 중 제일 아래



* 예시

```
<body>
	<header>
		<h1>레이아웃 나누기</h1>
		<em>오늘은 즐거운 목요일</em>			<!-- 글씨 기울이기-->
	</header>
	<nav>
		<strong>고르세용</strong><br>			<!-- 글씨 굵게-->
		<mark>먹고싶은거</mark>                 <!-- 형광펜 표시-->
		<ul>
			<li>메뉴1</li>					 <!-- 동그라미 리스트-->
			<li>메뉴2</li>
			<li>메뉴3</li>
			<li>메뉴4</li>
		</ul>
	</nav>
	<section>
		<article>
			<h2>제목1</h2>
			<p>내용1</p>
		</article>
		<article>
			<h2>제목2</h2>
			<p>내용2</p>
		</article>
	</section>
	<footer>
		<h3>홈페이지 정보(바닥 글)</h3>
	</footer>
</body>
```

* 레이아웃 분류 표시

```
<style>
	* {								<!-- 전체에 표시-->
		margin : 0
	}
	header {
		border : 1px dotted red;
	}
	footer {
		border : 1px dotted orange;
	}
	section {
		border : 1px dotted blue;		
	}
	article {
		border : 1px dotted green;
	}
	nav {
		border : 1px dotted magenta;
	}
	aside {
		border : 1px dotted brown;
	}
</style>
```



* 다른 링크에서 css 스타일을 가져다 쓸 때

```
<link rel="stylesheet"  href="mystyle.css">
```



* 수평선 꾸미기

```
hr {
            background-color : magenta;
            height : 10px;
        }
```



* 리스트 점 꾸미기

```
<style>
ul.a {
  list-style-type: circle;
}
ul.b {
  list-style-type: square;
}
ul.c {
  list-style-image: url('/edu/images/pink.gif');
}

# 숫자 리스트
ol.d {			
  list-style-type: upper-roman;
}
ol.e {
  list-style-type: lower-alpha;
}
</style>
```



* 각 레이아웃 속 글씨 가운데로

```
line-height : center;
vertical-align : middle;
text-align : center
```

