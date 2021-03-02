## 3/2 수업



### 주요 API

* Python `import` == `library()` : 패키지를 로드
  * `install.packages()`
  * `dplyr :: select`
  * `data()`: data set 로드

* `unique()`: 중복된 데이터 내용을 하나로

* `table(): `value들의 카운트!







#### 날짜와 시간관련 함수들

- 현재날짜: `Sys.Date()`
- 현재날짜 및 시간: `Sys.time()`
- 미국식 날짜 및 시간: `date()`
- `Date`: 날짜만

* `POSIXct` :  날짜 & 시간
* `POSIXlt` : 

- 년월일 시분초 타입의 문자열을 시간으로 변경
  - `as.Date`("년-월-일 시:분:초") 
  - `as.Date`("년/월/일 시:분:초")
- 특정 포맷을 이용한 날짜 및 시간: `as.Date("날짜 및 시간 문자열", format="포맷")`
- 날짜 데이터끼리 연산 가능 
  - 날짜끼리 뺄셈가능, 날짜와 정수의 덧셈뺄셈 가능 - 하루를 1로 간주, 소숫점 생략
  - 날짜 데이터끼리 연산할 때 소숫점을 표현하고자 하는 경우는 `as.Date` 대신에 `as.POSIXct` 함수를 이용



##### 특정 포맷

* `%d`:  day as a number (1-31) 01-31
* `%a`:  abbreviated weekday Mon
* `%A`: unabbreviated weekday Monday
* `%m`: month (01-12) 01-12
* `%b`: abbreviated month Jan
* `%B`: unabbreviated month January
* `%y`: 2-digit year 07





#### 문자열 처리 함수들

* `nchar()`
* `sort()`
* `tolower()`
* `toupper()`
* `substr()`
* `substring()`
* `grep()`
* `gsub("찾을 문자열","대체 문자열","대상 문자열")`: *대상 문자열*에서 *찾을 문자열*을 찾아 *대체 문자열*로 바꿔라~, 조건에 맞는 값을 찾으면 **찾을때마다 대체**(여러번)
  * `sub("찾을 문자열","대체 문자열","대상 문자열")`: 맨 앞에 있는 값만 대체
  * 대체문자열: "" 이면 삭제기능
* `strsplit()`





#### 정규표현식

> 범위로 일련의 데이터를 출력하기?

```
ABCDEFGHIJKLMNOPQRSTUVWXYZ	: [A-Z]
가각갂간...					 : [가-힣]

```

* `A*B`: AB, AAB, AAAB, B,...
* `A+B`: AB, AAB,AAAB,..........
* `A?B`: AB, B
* `[[:digit:]]` or `\\d`: Digits; [0-9]
* `\\D`: Non-digits; ` [^0-9]`` 
* ``[[:lower:]]`: Lower-case letters; [a-z]
* `[[:upper:]]`: Upper-case letters; [A-Z]
* `[[:alpha:]]`: Alphabetic characters; [A-z]
* `[[:alnum:]]`: Alphanumeric characters [A-z0-9]
* `\\w`: Word characters; [A-z0-9_]_
* `\\W`: Non-word characters
* `[[:xdigit:]]` or `\\x` : Hexadec. digits; [0-9A-Fa-f]
* `[[:blank:]]`: Space and tab
* `[[:space:]]` or` \\s`: Space, tab, vertical tab, newline, form feed, carriage return
* `\\S`: Not space; `[^[:space:]]`
* `[[:punct:]]`: Punctuation characters; !"#$%&’()*+,-./:;<=>?@[]^_`{|}~
* `[[:graph:]]`:Graphical char.;` [[:alnum:][:punct:]]`` 
* ``[[:print:]]`: Printable characters; `[[:alnum:][:punct:]\\s]`
* `[[:cntrl:]]`or `\\c`: Control characters; `\n`, `\r` etc.



#### apply 계열 함수

> 아규먼트로 함수 줄 수 있음

* `apply( )`: 배열 또는 행렬에 주어진 함수를 적용한 뒤 그 결과를 벡터, 배열 또는 리스트로 반환 
  * 배열 또는 행렬에 적용 
* `lapply( )`: 벡터, 리스트 또는 표현식에 함수를 적용하여 그 결과를 리스트로 반환 
  * 결과: 리스트 
* `sapply( )`: lapply와 유사하나 결과를 가능한 심플한 데이터셋으로 반환 
  * 결과: 심플데이터셋 
* `tapply( )`: 벡터에 있는 데이터를 특정 기준에 따라 그룹으로 묶은 뒤 각 그룹마다 주어진 함수를 적용하고 그 결과를 반환 
  * 데이터를 그룹으로 묶은 뒤 함수를 적용 
* `mapply( )`: sapply의 확장된 버전으로(multiple), 여러 개의 벡터 또는 리스트를 인자로 받아 함수에 각 데이터의 첫째 요소들을 적용한 결과, 둘째 요소들을 적용한 결과, 셋째 요소들을 적용한 결과 등을 반환 
  * 여러 데이터셋의 데이터를 함수의 인자로 적용한 결과