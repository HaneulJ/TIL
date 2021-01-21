

## 1/20 수업(2)_ JavaScript

### JavaScript

> 웹 페이지의 동적인 처리를 구현하는 프로그래밍 언어

1. 변수 정의 방법과 처리 가능한 데이터 타입
2. 연산자와 제어문
3. 배열(array) - 파이썬의 리스트와 비슷
4. 함수 정의 방법, 함수 사용 방법(호출): 함수는 일급 객체
5. 객체 생성 방법: 클래스 & { ... } _ 객체리터럴
6. 이벤트 처리 방법, DOM 객체를 통해서 HTML태그를 제어하는 방법
7. jQuery: JavaScript의 대표적인 API, 간단한 자바스크립트 구현을 지원

* 객체지향 언어

* `<script> </script>`
  * `console.log`

* HTML파일 안에 구현하는 프로그래밍 언어, 인터프리터 언어
* `<script> </script>`태그의 컨텐트로 작성하거나 HTML태그에 정의된 속성의 값으로 작성
* 파이썬, R과 비슷한 구문(인터프리터 언어)

* 값이 없는 literal: undefined, null
* 자바스크립트: true, false (대소문자 구분)

* API(Application Programming Interface): 프로그래밍할 때 자주 구현되는 기능들을 미리 구현해 놓은 프로그램
  * 프로그래밍 언어마다 자기만의 API를 가지고 있으며 개발 환경을 구축할 때 함께 설치되는 API를 표준 API라고 하며 개발자가 필요에 의해 추가로 설치하는 API들을 확장 API 또는 third-party API라고 한다.



#### JavaScript 제어문

* 조건제어문: `if`, `switch`
* 반복제어문: `for`, `while`, `do~while`
* 분기제어문: `break`, `continue`

* 예외처리 구문 지원: `try -- catch -- finally`

```
// if 제어문
if (조건식)
	수행문장;
	
if {(조건식)
	수행문장;
	수행문장;
	}
	
if (조건식)
	수행문장;
else if (조건식)
	수행문장;
```

```
// for 문
// 일반(전통) for일 때
for (초기식; 조건식; 증감식)		// 1.초기화식, 2.조건식, 3. 수행문장, 4.증감식
	반복수행문장
for(변수 정의와 초기와식; 반복처리를 계속 할지 결정하는 조건식; 변수의 값을 변화시키는 식)
for(var num =1; num < 11; num += 1)		//10번 반복
for(var num =10; num > 0; num -= 1)		//10번 반복
for(var num = 1; num <= 50; num += 1)	//몇 번 반복할지가 중요할 때

// 향상된 for, for-each, for in 일 때
for(변수 정의 in 배열 또는 객체)
	반복수행문장
	
a = [10,20,30,40,50]			// 배열, array
for(var i in a)
	window.alert(i)
0, 1, 2, 3, 4			// index가 출력

for(var i in a)
	window.alert[i]		// []대괄호여야 값이 출력
	
파이썬 경우:
>>> for data in a:
		print(data)
10 20 30 40 50 			# 값이 행단위로 출력
```

```
// while 문
while(조건식)
	반복문장;

while(true)
	무한반복문장;
```



#### 데이터 타입

* 문자열 string
* 숫자 number
* 논리 true, false
* boolean
* null, undefined 



#### 주요 연산자

* 수치 연산자
* 비교 연산자: `===`
* 조건 연산자
* 대입 연산자
* 비트 연산자
* 타입 점검 연산자: `typeof`
* 삭제 연산자



#### 예제 코드

* `button` 태그 라벨

```
<button>클릭하세요</button>
<button><img src="../images/kakao/g7.png"></button>
```

* 예제

```
<script>
	var v1;
	document.writeln(v1+"<br>");
	v1 = 100;
	document.writeln(v1+"<br>");
	v1 = '가나다';
	document.writeln(v1+"<br>");	
	var v1 = true;
	document.writeln(v1+"<br>");	
	v1 = 123;
	document.writeln(v1+45+"<br>");	
	v1 = '123';
	document.writeln(v1+45+"<br>");	
</script>

// document.writeln: 내보내기
// ""없이 특정문자가 나오면 변수로 인식
// 변수 생성 시: var 변수이름
// ""인용부호가 있으면 문자열
```

```
undefined
100
가나다
true
168
12345
```

* 예제

```
<script>
	document.write("<ul>");
	var v1;
	document.write("<li>"+ v1 +"</li>");
	document.write("<li>"+ typeof v1 +"</li>");
	document.write("<li>"+ (v1+10) +"</li>");
	v1 = 100;
	document.write("<li>"+ v1 +"</li>");
	document.write("<li>"+ typeof v1 +"</li>");
	document.write("<li>"+ (v1+10) +"</li>");
	v1 = true;
	document.write("<li>"+ v1 +"</li>");
	document.write("<li>"+ typeof v1 +"</li>");
	document.write("<li>"+ (v1+10) +"</li>");
	v1 = "가나다";
	document.write("<li>"+ v1 +"</li>");	
	document.write("<li>"+ typeof v1 +"</li>");
	document.write("<li>"+ (v1+10) +"</li>");
	document.write("</ul>");
</script>
```

* undefined
* undefined
* NaN                            // not a number
* 100
* number
* 110
* true
* boolean                   // true: 1, false: 0
* 11
* 가나다
* string                      // 문자열 객체: string class
* 가나다10                // 숫자가 문자열로 바껴서 출력

```
<pre>
<script>
	document.writeln(10>5);
	document.writeln("abc">"ABC");
	var str = "가나다";
	document.writeln(str == "가나다");
	document.writeln(true == 1);		// true = 1로 바뀜
	document.writeln("100" == 100);     // type을 맞춰서 처리( 숫자를 문자열로 ), 타입이 다를 때 이용
	document.writeln(true === 1);       // ===:동치연산자, 두 피연사자들의 타입 확인 -> 값 비교 (타입 다르면 무조건 false)
	document.writeln("100" === 100);	
	document.writeln(10/3);
	document.writeln(10%3);
	var num=10;							// ++와 --의 위치 중요
	document.writeln(num++); // 10      // 10 출력 후 1 증가한 11로 넘김
	document.writeln(--num);  // 10     // 1을 먼저 감소시킨 후 10 출력
</script>
</pre>
// writeln: 끝에 개행문자를 붙여라 -> 빈칸 한 개로 인식
// <pre>: <br>태그를 쓰지 않았음에도 개행 가능, 폰트사이즈 작아짐
```

```
true
true
true
true
true
false
false
3.3333333333333335
1
10
10
```

* 증감 연산자(++, --): 주어진 피연산자의 값을 1증가/감소
  * ++변수: 변수의 값을 1 증가시키고 다른 연산을 수행
  * 변수++: 다른 연산을 먼저하고 나중에 변수의 값을 1 증가

```
<script>
	var num=window.prompt("숫자 하나를 입력해 주세요");
	window.alert(num)
	// num이 짝수이면 "xx는 짝수"
	// num이 홀수이면 "xx는 홀수"
	num % 2 == 0 && document.writeln(num+"는 짝수");
	num % 2 == 0 || document.writeln(num+"는 홀수");
</script>

// var num=window.prompt 팝업창을 띄워 사용자에게 데이터 하나를 입력받아서 리턴
// 입력내용은 문자열로 인식
// &&: and 연산자 
// ||: or 연산자
// if (num % 2 == 0)
		document.writeln(num+"는 짝수");
	를 간단하게 표현한 것
```

```
window.alert(num+":"+isNaN(num));
// 숫자타입이 맞게 들어오는지 확인
// false: 맞게 들어옴

num = num.trim()
// 앞이나 뒤에 있는 빈칸 제거
```

```
// if문은 수행문장이 2개 이상일 경우 {}로

if(isNaN(num) || num == '' || num == null ) {
		document.writeln("<span>숫자</span>를 입력해 주세요!!!");
	} else {
		num % 2 == 0 && document.writeln(num+"는 짝수");
		num % 2 == 0 || document.writeln(num+"는 홀수");
	}
```

```
// for문 (초기식; 조건식; 증감식)

for(var su=1; su < 4 ; su++ ) {

// su++ 
// su += 1
// su = su + 1
// 다 같음
```

```
// 사용자가 원할 때까지 반복

var result = window.confirm("계속 수행할까요?");
if(!result)			// 파이썬의 not 연산자와 동일
break;
```

* `window.alert()`: 사용자에게 메세지를 보여주고 확인 받는 용도
* `window.prompt()`: 사용자로부터 데이터를 입력받는 용도
* `window.confirm()`: yes 또는 no 둘 중 하나를 입력받는 용도		



* `Math.random()`: 랜덤 값 구하기(0.0<= rand < 1.0)
* `Math.floor(rand*3);`: 소숫점 이하를 날리고 출력 0, 1, 2 중 하나!
* `rand*n+1`: 0~n 사이 난수 추출

