## 1/15 수업

### HTML 태그학습

* 대소문자 구분X
* `?`: url과 query 구분 문자

```
# 특수문자 엔터키:<>를 사용하고 싶을 때
&lt;~~~&gt;
```

```
# 개행문자: <br>
# 종료태그 따로 없음
```

```
# 단락 나누기: <p></p>
```

```
# 계정과 패스워드
<form mthod="get" action="http://localhost:8000/edu/serverprogram">
    계정 <input type="text" name="account" required>
    패스워드 <input type="password" name="pwd" required>
    <input type="submit" value="로그인">
    <input type="reset" value="재작성">
</form>

# action뒤의 주소는 가상
# required: 필수 작성
```

```
# checkbox: 복수선택 가능
# radio: 하나만 선택 가능

<form mthod="get" action="http://localhost:8000/edu/serverprogram">
    좋아하는 음식: <br>
    <input type="checkbox" name="food" value="불고기">불고기<br>
    <input type="checkbox" name="food" value="치킨">치킨<br>
    <input type="checkbox" name="food" value="피자">피자<br>
    <input type="checkbox" name="food" value="짜장면">짜장면<br>
    
    좋아하는 색깔: <br>
    <input type="radio" name="fcolor" value="노란색">노란색<br>
    <input type="radio" name="fcolor" value="초록색">초록색<br>
    <input type="radio" name="fcolor" value="주황" checked>주황색<br>

    <input type="submit" value="전송">
    <input type="reset" value="재작성">
</form>

# name과 value를 content와 맞춰야 함
# value: 퀴리문자 구별
# <>뒤에 이름: 사용자에게 보여지는 이름
# checked: 미리 체크되어 표시됌
```

```
# 숫자만 받는 type: number
# 최소, 최대숫자 지정 가능
태어난 년도를 입력하세요:<br>
    <input type="number" name="age" min="2000" max="2005"><br>

    <input type="submit" value="전송">
```

```
# 스크롤로 선택 가능: 하나만(복수선택 시 다른 설정)
태어난 년도를 입력하세요:<br>
  <select name="year">
      <option value="2000">2000</option>
```

```
# 글 쓸 때?
남기려는 글을 입력하세요: <br>
<textarea name="memo" row="5" cols="50"></textarea>
```

```
# 달력 표시(년 월 일 시 포함): datetime-local
<input type="datetime-local" name="birth"><br><br>

# 년월일 포함(시간 제외): date
<input type="date" name="birth"><br><br>
```







#### 꾸미기 style

```
# 인라인 방식: 시작태그의 속성으로 작성
<h1 style="color:red">~~~</h1>
```

```
# h2마다 같은 색을 지정하고 싶을 때(전역적인 방법): <head>~~</head>에 작성!!!
<head>
    <style>
        h2{
        color : green;
        }
    </style>
</head>
```

> 전역, 인라인방법 둘 다 지정되어있을 때는 **우선순위 1. 인라인 2. 전역**



```
# 글씨색, 배경색, 가운데정렬
<h1 style="color:red; background-color:skyblue;text-align:center">주요 HTML 태그 학습</h1>
```

```
# 글씨 그림자: 옆 아래 번짐효과크기 컬러
text-shadow: 2px 2px 3px

# 폰트사이즈: 기본크기에 ~배수 or (~~pt)
font-size:4em;

```

```
# 하이퍼링크 밑줄 제거(전역) , 태그 간의 간격
a{
text-decoration:none;
margin-right:30px;
}

# 단위:0값을 제외하고 생략 불가
```

```
# 마우스를 가져다댈 때 굵게 표시
a:hover{
            font-weight:bold;
        }
        
# 마우스를 댈 때 사진의 투명도(투명해짐)
img:hover{
            opacity:0.3;
            }
            
# 위와 반대, 마우스를 댈 때 사진이 나타남
img:hover{
            opacity:0.3; /*0.0~1.0*/
            }
```

```
# HTML 주석
<!--			-->
```

```
# %는 브라우저 크기에 따라 변화함
img{
            width:30%;
        }
```



```
# 블럭 스타일 태그: 행단위로 출력
<div></div>
:p, div, h1, h2, h3, h4, h5, h6, form 등

# 인라인 스타일 태그: 하나의 행에 이어져서 출력
<span></span>
:img, span, input 등

태그에 부여하는 사이즈 지정법이 다름
```

```
margin-top, margin-right, margin-bottom, margin-left
margin: 10px20px30px40px	# 위 오른쪽 아래 왼쪽
margin: 10px20px30px		# 위 아래 좌우
margin: 10px20px			# 위아래 좌우
margin: 20px auto			# 위아래20 좌우는 자동(가운데정렬)
```

```
div:nth-of-type(1) 		# 첫번째 div

border-radius: 30px		# 모서리를 다 30px만큼 완만
border-radius: 20px 40px 60px 80px		#왼쪽 top부터 시계방향
border 스타일: dotted
```

```
# 배경 그라데이션
background-image : linear-gradient(to bottom, yellow, green)

# 배경 이미지
background-image : url("/edu/images/pink.gif");		
```

```
# 그림배경 안에 글씨를 정가운데 맞추기
padding-top:~px;
margin:center;
```







### 웹클라이언트

#### CSS(Cascading Style Sheets)

> 구조적으로 짜여진 문서(HTML, XML)에 style을 적용하기 위해 사용하는 언어

* 스타일은 요소 표시 방법 및 페이지에서의 요소 위치 지정

* W3C의 표준
* CSS사용한 웹페이지 개발 가능
* 확장성, 편의성, 재사용성, 생산성
* 작성법: 인라인, 전역적, 외부파일연결(head에) 방법



* CSS 선택자(selector): 스타일을 적용하기 위해 대상 선택
* 전체 선택자: 페이지에 있는 모든 요소 대상으로 스타일 적용

```
*{amrgin:0; padding:0}
```

* 태그 선택자: 문서 안의 특정 태그에 스타일 모두 적용

```
p{font-size:12px; font-family:"돋음";}
```

* 클래스 선택자: 문서안에 여러번 반복할 스타일일 때, 클래스 선택자로 정의 `.` 뒤에 클래스 이름 지정

```
.redtext{color:red;}
```

* id 선택자: 문서 안에서 한번만 사용할 때, id 선택자로 정의 `#` 뒤에 id 이름 지정

```
#pic2{clear:both; float:left;}
```

* 하위 선택자: 부모요소에 포함된 모든 하위 요소에 스타일 적용

```

```

* 그룹 선택자: 같은 속성을 적용해야 할 경우 한번에 묶어서 정의

```
a,p{color:#fffff}
<로 선택자 구분
```

* 속성 선택자
  * [속성] : 지정한 속성을 가지고 있는 요소를 찾아 스타일 적용
  * [속성 ~= 값] : 속성과 값을 체크해 여러 개의 값 중 하나만 일치해도 스타일 적용
  * [속성 ^= 값] 
  * [속성 *= 값]
  * [속성 $= 값] : 속성의 값이 지정한 문자로

```
img[src$=png]
```

* 가상 선택자










#### CSS3

> 모듈 기반 개발
>
> text, fonts, color, background&borders, transforms, transitions, animations

* 구조 선택자 지원
* 가상 선택자 지원
* 둥근 모서리의 경계선 지원: `border-radius`
* 그라데이션 배경 지원
* 변환, 전환, 애니메이션 지원
* 글자와 박스 뒤에 그림자 효과 지원