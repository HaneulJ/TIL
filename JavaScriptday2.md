## 1/21 수업

* 파이썬 주석: `#`

* html 주석: `<!-- -->`
* CSS 주석: `/* */`
* JavaScript 주석: `/* */`, `//`



* `undefined ` = `false` (boolen 형에서)

* `Math.random()`: 0~1사이 난수 추출
* `Math.floor()`: 소숫점 이하 날리기 (실수를 정수로)

* 올림

```
var num = Math.floor(Math.random()*10) + 1
```

* `typeof ~`: object 객체다
* `document.write`: 출력만
* `document.writeln`: 출력 + `<br>`



#### for 문

* `for` 반복문: 초기식, 조건식, 증감식으로 구석되는 for문
  * `for(초기식;조건식;증감식)`

* `for in` 반복문: 배열이나 객체를 가지고 반복을 처리하는 for문
  * `for(인덱스(키)를 저장할 변수 정의 in 배열 또는 객체)`





### 배열

> 여러 데이터들을 하나의 묶음으로 다루고자 할 때 사용
>
> 파이썬의 리스트 객체와 거의 동일

* 묶을 수 있는 데이터의 객수 제한 거의 X, 데이터 타입 제한 X
* 자바스크립트의 배열도 객체로 취급



#### 배열 생성 방법과 배열 사용 방법

* 배열 생성방법
  1. 배열 리터럴 방법: `[1,2,3,4,5 ...]`, `["aaa", 100, true]`, `[]`
     * `[8]`: 8이라는 값을 가진 하나의 배열로 인식
  2. API를 이용하는 방법: `new Array [1,2,3,4,5 ...]`,  `new Array ["aaa", 100, true]`,  `new Array []`
     * `new Array [8]`: 8을 배열의 크기로 인식, 8개의 빈칸 undefined 생성 



* 배열 사용방법
  * 배열의 크기(배열을 구성하는 엘리먼트의 갯수): 배열 객체의 length라는 속성(변수)의 값 사용
  * 배열의 요소(원소, 엘리먼트) 접근(l-value, r-value 모두 가능): `[0부터 시작하는 인덱스]`, 음수 지원 X



* `Array.isArray(a1)`: true 배열이다	

* `a1[4] = 100;` a1의 5번째 원소는 100이다.

  * [ , , , , 100] : 4개의 undefined와 5번째의 100인 배열 생성

  * ```
    for(var i=0; i < a1.length; i++)
    	document.write("<h4>"+ a1[i] +"</h4>");
    // undefined값도 출력
    ```

  * ```
    for(var i in a1)  
    	document.write("<h4>"+ a1[i] +"</h4>");
    // undefined값은 무시함
    ```

* `var a2 = [10, '가나다', true, 3.5];`의 경우

  * ```
    for(var i in a2) 
    	document.write("<h4>"+ typeof a2[i] + ":" + a2[i] +"</h4>");
    
    number:10
    string:가나다
    boolean:true
    number:3.5
    ```

* 파이썬의 `str` = `toString`

* `Date` 객체는 `toString`을 포함

```
var d = new Date();
document.write(d.toString() + "<br>");
document.write(d + "<br>");

// 같은 결과값이 나옴
```

* `.sort()`: array 객체 안에 있는 데이터들 순서대로
  * 숫자는 문자열처럼 정리해서 크기순대로 X: optional compareFunction
  * `.sort(function(a, b){ return a-b;})`: 숫자를 크기순으로 
  * `.sort(function(a, b){ return b-a;})`: 숫자를 역순으로

* `.push()`: 파이썬 리스트의 `append()`와 비슷





### 함수

> 자주 사용되는 코드를 묶은 단위
>
> 일급 객체 만족



#### 함수 만드는 방법

* 선언적 함수정의(명시적 함수정의)

```
function 함수명([매개변수..]) {
	함수의 수행 코드들
	return 리턴값;
	}		
```

* 함수 표현식(함수 리터럴)

```
변수 = function 함수명([매개변수..]) {
		함수의 수행 코드들
		return 리턴값;
		}	
```

*  일급객체로 취급
  * 함수를 변수에 담아서 사용(호출) 가능
  * 함수 호출 시 아규먼트로 전달 가능
  * 리턴값을 함수로 전달 가능

* 함수를 호출할 때 함수에 정의된 매개변수만큼 아규먼트를 전달하지 않아도 호출 가능

* 함수가 값을 리턴하지 않으면 undefined가 자동으로 리턴

* 가변인수 지원: 함수 호출시 아규먼트 갯수에 제한X 함수 생성 가능
  * 가변인수 함수를 정의할 때는 매개변수 정의를 생략하고 함수 호출 시 자동으로 만들어지는 arguments라는 배열 활용

* 기본값을 갖는 매개변수 정의 가능



#### 함수 사용 방법(호출, r-value)

```
함수명([아규먼트...]);
var r = 함수명([아규먼트...]); 
```



* 자바스크립트는 전역변수&함수정의 먼저 해석

```
// 비어있는 `f1()`를 먼저 입력해도 `function f1`
f1();
document.write("<hr>")
var f1 = function () {
	document.write('f1() 호출<br>');	
```

```
// 함수 표현식을 만들어서 변수에 담는 방식으로 함수를 정의했을 경우에는 불가
f1();
document.write("<hr>")
var f1 = function () {
	document.write('f1() 호출<br>');	
}
var f2 = function (p1, p2) {
	document.write('f2() 호출-'+(p1+p2)+'<br>');	
}
```



* undefined는 타입과 값이 같음
  * `typeof p == "undefined"`  =  `p == undefined`
  * 타입 연산자는 원래 `" "`문자열로 비교해야함
* `{ }`: 객체
* `[ ]`: 배열 객체
* `arguments.`: 가변인수를 가진 함수를 만들 때 자동 생성

* `console.log(' ')`: 콘솔 창에 행단위로 출력(브라우저 화면에 출력X, 개발자를 위한 서비스)
* 예시

```
function out() {
	document.write("아규먼트 갯수 : "+arguments.length+"<br>");
	for(var i=0; i < arguments.length; i++) 
		console.log(arguments[i]);
	 ;
}
out();
out(10);

아규먼트 갯수 : 0
아규먼트 갯수 : 1
```

* 아규먼트로 고차함수 전달

```
function output(p) {
	if(typeof p == 'function') {
		p("ㅋㅋㅋ");
	} else {
		document.write("<h2>ㅋㅋㅋ : "+p+"</h2>");		
	}	
}
output("둘리");
output(function(param) { console.log(param);})
```

```
function myAlert(param) {
	window.alert(param);
}
output(myAlert);

// 위 아래 같은 식

var myAlert = function(param) {	
	window.alert(param);
}
output(myAlert);
```



* `window.setInterval(함수, 밀리세컨단위의 초시간)`: ~초시간 마다 한번씩 함수 호출
  * `var time = 5000;` 5초
* `.toLocaleString()`: local에 맞게 문자열로 표시