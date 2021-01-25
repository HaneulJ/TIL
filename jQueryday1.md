## 1/25 수업

실습 리뷰

* 자바스크립트는 **곱셉**연산자가 있을 시 **자동으로 숫자문자열을 숫자로** 변경하여 연산



* `a`: 이벤트 핸들러 내장
  * 인라인 이벤트: 함수등록X, 수행 코드 등록
  * 디폴트 이벤트 핸들러: 기본으로 내장, 무시하고 싶을 때는 `return false`
  * `.preventDefault()`: 기본 이벤트 핸들러를 해지할 때
* `.querySelector` = `.getElementById`
* `onload`: 페이지에 대한 처리가 끝나면~
* `setTimeout({}, 5000)`: 5초 후에 가동





### [jQuery]

> HTML문서 안의 스크립트 코드를 단순화하도록 설계된 자바스크립트 라이블리

* DOM 요소 선택 기능, 탐색 및 수정
* CSS 셀렉터에 기반한 DOM 조작
* 자바스크립트로 만들어진 다양한 함수
* `<script src="~~"></script>`
* 메서드 호출방식

  * `jQuery(자바스크립트객체).xxx()`
  * `jQuery.xxx()`
  * `jQuery` = `$`
  * `$('CSS선택자').xxx()`
  * `$(함수)` : 로드 이벤트 발생시 호출될 함수 등록 = `$(document).ready(function(){...})` 모든 이벤트 핸들러 등록
  * `$.xxx()`: jQuery 객체가 제공하는 클래스 메서드 
  * `("HTML 태그 문자열")`
* `$("dom 객체").click(함수)`
* `$('ul *').css('color', 'red');`: ul 태그의 모든 자손 태그(ul은 빠지고)의 색상 지정
* `$('body > div > div').css('font-weight', 'bold');`: 자식 태그
* 표준 이벤트 핸들러 사용
* `$()` 함수

* `$(" ").addClass(function (index) {~`: "~"에 속성 추가
* `$(" ").each(함수)`: for문과 비슷



* API 사용방법이 일관성 있어 API를 익히기 쉽다.
  * `html()` : `innerHTML`
  * `text()`: `textContent`
  * `val()`: `value`
  * `css()`
  * `attr()`
* **getter 값을 읽는다**
  * `html()`	- 첫번째만 수행
  * `text()`    - 모두
  * `val()`      - 첫번째만 수행
  * `css("CSS속성명")`
  * `attr("HTML태그속성명")`
* **setter 값을 설정한다**
  * `html("...")`  /  `html(함수)`  
  * `text("...")`  /  `text(함수)`
  * `val("...")`   /   `val(함수)`
  * `css("CSS속성명", "CSS속성값")`  /  `css("CSS속성명", 함수)`  /  `css(자바스크립트객체)`
  * `attr("HTML태그속성명", "HTML태그속성값")`  /  `attr("HTML태그속성명", 함수)`  /  `attr(자바스크립트객체)`



* `$('h1').html(function (index, html) {`: index자리에 다른 명이 와도 무조건 인덱스가 출력



#### jQuery 이벤트 핸들러 구현

* `$("...").on("이벤트이름", 함수)`
* `$("...").on(자바스크립트객체)`

* `$("...").off()`: 이벤트 핸들러 해제

* `$("...").이벤트이름(함수)`



```
// 같은 결과 나옴
$('h1').on({
                mouseenter: function () { $(this).addClass('reverse'); },
                mouseleave: function () { $(this).removeClass('reverse'); }
            })
 
 
$('h1').hover(function () {
                $(this).addClass('reverse');
            }, function () {
                $(this).removeClass('reverse');
            })
```



#### Geolocation API

`window.navigator.geolocation 객체`  

> 위치요청에 대해 사용자가 동의하면 브라우저의 위치 정보가 반환된다.

* `getCurrentPosition()` : 현재 위치정보를 추출
* `getCurrentPosition(successCallback[, errorCallback, options])`
  * `successCallback` : 위치정보를 성공적으로 추출했을 때 호출되는 콜백 함수
  * `errorCallback` : 위치정보를 추출하는데 실패했을 때 호출되는 콜백 함수
  * `watchPosition()` : 주기적으로 반복해서 위치정보를 구하는 작업을 수행
  * `watchCurrentPosition(successCallback[, errorCallback, options])`

