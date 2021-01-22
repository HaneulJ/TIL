## 1/22 수업

* 자바스크립트 for문: `for(var key in 배열)` 일 때 `key`는 인덱스라 `배열[key]`로 꺼내야 값이 호출 됌

* `setTimeout`: 몇 초후에 한번 사용
* `setIntervalTimeout`: 몇 초마다 사용



#### [참고사이트]

https://htmlcheatsheet.com/js/

https://htmlcheatsheet.com/css/

https://htmlcheatsheet.com/



#### HTML에 자바스크립트 쓰는법

* `<script> </script>`

* `<script src="~~.js"></script>`: 독립된 파일로 만든 후 import, 먼저 정의해줘야함!

* ```
  <script> 
  	function()
  </script>
  
  <script> 
  
  </script>
  
  // 위에서 함수를 정의해야 아래 script에서 사용가능
  ```

* 상위 디렉토리에 있는 파일을 쓸 때: `<script src="../~~.js"></script>`, `<script src="/edu/jsexam/~~.js"></script>` 등



#### 변수정의

* 전역변수와 지역변수의 개념이 없었음
* `var 변수`로 선언해야 전역변수와 지역변수가 구별됌
* ECMA ver.5 부터 `let`, `const` 추가
  * `let`: 같은 이름의 변수가 2번 이상 선언되는 것을 방지
  * `const`: 변수를 상수로 사용(한번 할당된 값은 고정)
* `try ... catch() `: 파이썬의 `try...except`와 동일





#### 자바스크립트의 객체 생성 방법

* **객체 리터럴** 방법
  * 배열 객체: `[1, 'ABC', true, 3.4]`
  * 객체: `{속성명 : 속성값, 속성명 : 속성값,...}`, `{ }`
  * 속성명: 자바스크립트의 식별자 규칙(명명규칙), 문자로 시작, 문자/숫자/_ 사용 가능, unique해야함(key처럼)
  * 속성값: 숫자, 문자열, 논리값, 배열, 객체, 함수(메서드)

```
obj = {속성명1:100, 속성명2:"둘리", 속성명3:function(){...}}
obj.속성명1 = 200
obj.속성명2 + "승리"
obj.속성명3()		

obj['속성명1'] = 200
obj['속성명2'] + "승리"
// 호출은 .연산자(멤버 연산자)만 가능
```

```
var user3 = { father : {name : "고길동",age : 40}, son : {name : "희동이",age : 2} }

user3.son.name
희동이
// 속성값으로 객체가 올 수 있음
```

* **클래스(생성자 함수)를 이용**하는 방법: `new Array()`, `new Date()`

* **내장 객체**: 개발자가 객체를 생성하지 않아도 자바스크립트 엔진이 자동으로 생성해주는 객체
  * `window.`, `document.`, `navigator.`, `screen.`, `DOM ` 객체들





#### DOM(Document Object Model) 프로그래밍

> HTML를 구성하는 각각의 태그들을 자바스크립트로 구성
>
> 생성되는 DOM객체: 부모-자식 관계 적용 > 트리구조로 구성

* 모든 브라우저가 지원: 웹페이지 해석, 랜더링

```
<body>
	<h1>....</h1>
	<ol>
		<li>..</li>
		<li>..</li>
	</ol>
</body>

// 각각 DOM 객체
// document
	 body
  h1      ol
  		li   li
```



* DOM 객체 타입: Element타입, Attribute 타입, Text 타입



* 동적인 처리를 하려는 태그의 DOM 객체를 찾는 방법
  *  `document.getElementsByTagName("태그명")`: DOM 객체배열
  *  `document.getElementByTagId("id 속성값")`: DOM 객체
  *  `document.getElementsByClassName("class 속성값")`: DOM 객체배열
  * `document.querySelectorAll("CSS 선택자")`: DOM 객체배열
  * `document.querySelector("#CSS 선택자")`: DOM 객체
  * 객체배열: 비어있는 배열 출력 가능
  * 객체: Null(객체 없음), (undefined: 값 없음)



* 찾은 DOM 객체를 가지고 필요한 동적처리 구현하는 방법

  * 컨텐트 변경하기 (현재 값 읽을 때도 씀): `dom.innerHTML = "<p>새로운 내용</p>"` (꾸미기 그대로 들어가려면), `dom.textContent = "새로운 내용"` (컨텐트만 적용)

  * 스타일 바꾸기: `dom.style.CSS속성명 = CSS속성값`

    * `dom.style.background-color = "yellow"`: 불가
    * `dom.style.backgroundColor = "yellow"`: 가능
    * `-` 기호 대신 대문자로 표시!

  * 이벤트 핸들러 등록하기

    * 이벤트 핸들러에서의 `this`: 이벤트타겟 객체
    * 그 외의 `this`: window 객체 
    * `this.`: 변수의 아규먼트로 이용

    1. **인라인 이벤트 모델**(지역적 방식): 태그마다 속성으로 정의

       `<태그명 on이벤트명 = "이벤트 핸들러 코드">`

    2. **고전 이벤트 모델**(전역적 방식): `<script>` 태그 안에 정의

       ```
       DOM 객체를 찾는다.
       dom.on이벤트명 = function() {......}
       ```

    3. **표준 이벤트 모델**(전역적 방식): `<script>` 태그 안에 정의

       ```
       DOM 객체를 찾는다.
       dom.addEventListener("이벤트명", function() {......})
       ```

    

```
// 동일한 결과

alert(dom2.textContent);
alert(this.textContent);
alert(e.target.textContent);
```

* 
  * 고전이벤트와 표준이벤트의 차이
    * 고전이벤트 핸들러: 함수 하나만 가능
    * 표준이벤트 핸들러: 여러 개의 함수 가능

```
dom1.onclick = function () {
							alert("첫 번째 핸들러 수행(고전)");
							  };
dom1.onclick = function () {					
							alert("두 번째 핸들러 수행(고전)");
							  };
dom2.addEventListener("click", 
			function () { alert("첫 번째 핸들러 수행(표준)");});
dom2.addEventListener("click", 
            function () { alert("두 번째 핸들러 수행(표준)");});
            
// dom1:두 번째 핸들러 수행(고전)
// dom2: 첫 번째 핸들러 수행(표준)
         두 번째 핸들러 수행(표준)
```



* `<body onload="myf()">` : 이 페이지 로딩이 끝나면 `myf()` 호출해줘

* 속성의 값 추출 방법: `dom4.getAttribute("src")`(가공된 값),  `dom4.src`(값 그대로)

  

#### location

> 현재 보고있는 url정보를 담고있는 속성

```
// 동일한 결과를 나타냄
location.href = document.getElementById("choice").value;
location.href = document.querySelector("#choice").value;


<select id="choice" onchange="go(this);">
	function go(p){
	location.href = p.value}
```

