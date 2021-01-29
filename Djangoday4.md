## 1/29 수업

* 이미지 파일에 url를 줄 때
  * ` src="{% static 'images/olaf1.png' %}"` : Django에서 제공하는 `static`태그에서 ' ~ '라는 이미지를 로드
  * `src= "/static/images/olaf1.png"` : 하드코딩(값을 고정)
  * `static`: 정적자원을 주는, 클라이언트에 주기만 하면 O
* 정적 자원: 



* `<form action="{% url 'view 이름' %}" method="GET">`: `view이름`의 url로 이동
* 서울시 빅데이터
  * http://openapi.seoul.go.kr:8088/796143536a756e69313134667752417a/json/LampScpgmtb/1/100/
  * http://openapi.seoul.go.kr:8088/796143536a756e69313134667752417a/xml/LampScpgmtb/1/100/



### XML

> Extensible Markup Language
>
> 규격화 시킨 문서를 만들고 싶을 때 사용

* XML선언부를 제외하고 기존 HTML5의 기본 구조와 거의 유사
* 태그명을 용도에 맞게 직접 정의하여 사용 가능



### JSON

> JavaScript Object Notation
>
> 인터넷에서 자료를 주고받을 때 그 자료를 표현

* 자료의 종류 제한 X
* 컴퓨터 프로그램의 변수값을 표현하는데 적합
* 프로그래밍 언어와 플랫폼에 독립적, 서로 다른 시스템간 객체 교환 수월
* 개방형 표준, 읽기 및 쓰기 쉬움
* 문자열 표현 할 때 `" "`만 지원
* `{key : value}`



### AJAX

> Asynchronous JavaScript ans XML
>
> 빠르게 동적 웹페이지를 생성하는 기술

* 재로드(refresh)하지 않고 웹페이지의 일부만을 갱신하여 웹서버와 데이터 교환
* 동기통신
* 서버에 데이터를 보내고 현재 페이지에 반영 가능?
* origin 서버가 아니면 AJAX로 요청한 컨텐츠 수신X(서버 컨텐츠를 보호하기 위해)
* Cross Origin Resource Sharing(CORS)이면 Origin이 아닌  다른 사이트의 자원을 접근하여 사용 가능

```
reponse.addHeader("Access-Control-Allow-Origin","*");
```





#### jQuery에 AJAX 지원 API

* `$.ajax()`: 모든 Ajax 메소드의 기본 메소드
  * url, type 등
* `$.get()`
* `$.post()`
* `$.getJSON()`: JSON형식으로 응답 받는
* `$.load()`: 서버로부터 데이터를 받아서 일치하는 요소 안에 HTML 추가
  * `$.load(url,[, data][,function(data)])`
* `$.getScript()`: 자바스크립트 형식으로 응답 받는
* `$.ajaxSetup()`: 메소드 선택 사항들에 대한 기본값 설정

* `$.each(자바스크립특 객체, 함수` = `$('CSS선택자').each(함수)`



#### AJAX 프로그래밍 핵심 내용

* JSON(XML) 형식으로 응답하는 뷰를 준비 해야한다.
  * 템플릿을 거치지 않고 뷰가 직접 응답
* JavaScript만 사용해서 AJAX 요청을 구형하는 방법

```
var xhr = XMLHTTpRequest()
xhr.onload = 함수
xhr.open("GET", 요청하려는 대상 url, true)		# 택배 운송장만 붙인 상태
xhr.send()
```



* jQuery API를 사용하여 AJAX요청을 구현하는 방법

```
$.getJSON("대상 url", 함수)
```







* exam20 예제(`.getJSON`)

```
<script>
$(document).ready(function () {
  $('p').click(function(e) {
       $.getJSON('/secondapp/json3/',  function(data) {
             content = "";
        $.each(data, function(key, value) {
              content += value + "<br>";
        });
        $(e.target).html(content);
   });
  });
});
</script>

<!-- 
$('p').click(function(e): 매개변수e를 정의해서 이벤트 객체 전달 가능

$.getJSON('/secondapp/json3/',  function(data) : 반드시 function(data) 불러내야 java로 구현 가능?

$.each(data, function(key, value) {
              content += value + "<br>";
        }: for 문 대신, data의 개수만큼,
        		        console.log("key:" +key+"value:" +value);로 확인 가능
        
-->
```

* exam21 (객체로 자바스크립트를 줌): http://jsonviewer.stack.hu/ 사용

```
$.ajax({
       type : 'get',
       url : 'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=75474bdfc6c0a4eb738939dd66c101b5&targetDt=20210127',
       dataType : 'json',
       error: function(xhr, status, error){
           alert(error);
       },
       success : function(json){
           console.log(json)
           $('div').html(JSON.stringify(json))
           console.log(json.boxOfficeResult.dailyBoxOfficeList[0].movieNm)
       }
   });

// function(json): 객체정보 출력
// .html(JSON.stringify(json)): 객체를 문자열로 
// 위와 아래 식 동일 결과 나타냄

$.getJSON('http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=75474bdfc6c0a4eb738939dd66c101b5&targetDt=20210127',
        function(json){
            console.log(json)
            $('div').html(JSON.stringify(json))
            console.log(json.boxOfficeResult.dailyBoxOfficeList[0].movieNm)
        }
    );
```

* `targetDt`: xxxx년 xx월 xx일
* `var year = date.getFullYear();`: 4자리 연도
* `var month = (1 + date.getMonth());`: 0월부터라 +1 필수

* `const d = today.getTime() - (n*24*60*60*1000);`
* `encodeURIComponent(addr)`: 한글 인코딩해주는 함수,,





* 구글맵은 자바스크립트에서 사용 가능
* 자바스크립트에서 Django 변수 사용 가능