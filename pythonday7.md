## 1/12 수업

### 문자열 분리

#### 첨자

> 문자의 위치

* 대괄호와 첨자를 적어 문자열을 구성하는 개별문자 읽음
* 앞뒤 양쪽에서 읽을 수 있음
* for문으로 순회하여 개별 문자 순서대로 꺼냄



#### 슬라이스

> 범위 지정하여 부분 문자열 추출

* `[begin:end:step]`
* 일정 형식 가진 문자열에서 원하는 정보만 추출 가능



#### 메서드

> 클래스에 소속된 함수

* 객체에 대해 특화된 작업 수행



#### 검색

* `len()`: 문자열 길이 조사
* `find`: 인수로 지정한 문자 또는 부분 문자열의 위치 조사
* `rfind`: 뒤에서 검색 시작
* `count`: 특정 문자 개수





### 문자열 메서드

#### 조사

* `in` 구문: 특정 문자 유무 여부 조사
* `isalpha ` 알파벳 / `islower`  소문자 / `isupper` 대문자 등



#### 변경

* `lower` / `upper`: 각기 영문자를 전부 소문자 / 대문자로 바꿈

* `lstrip`: 왼쪽/ `rstrip`: 오른쪽 / `strip`: 양쪽 공백 제거



#### 분할

* `split`: 구분자를 기준으로 문자열 분할
* `splitlines`: 개행 문자나 파일 구분자 등 기준으로 문자열 잘라 리스트로 만듦
* `join`: 문자열의 각 문자 사이에 다른 문자열 끼워넣음 





#### 대체

* `replace`: 특정 문자열을 찾아 다른 문자열로 대체 (검색할 문자열, 바꿀 문자열)
* `just`: 문자열을 특정 폭에 맞춰 정렬
* `center`: 중앙 정렬









### 포맷팅

#### 포맷팅 `format % values`

> 문자열 사이사이에 다른 정보 삽입하여 조립하는 기법

```
>>> print = 500
>>> print("궁금하면 %d원" % price)
```

* `%d`: 정수
* `%f`: 실수
* `%s`: 문자열
* `%c`: 문자 하나
* `%h`: 16진수
* `%o`: 8진수
* `%%`: % 문자

* `%[-]폭[.유효자리수]`
* 폭에 `-` 지정하여 왼쪽 정렬
* `.`기호로 소수점 이하 표시 자리수 설정

> * string cat
> * `format % values`
> * `'{}'.format()`
> * `f-Strings`

```
>>> stname = "유니코"; stage=20; stavg=95.869
>>> print(stname+"학생은 나이가 "+str(stage)+"이고 평균은 "+str(stavg)+"입니다") 
>>> print(stname, "학생은 나이가 ", stage, "이고 평균은 ", stavg, "입니다", sep="") 
>>> print("%s학생은 나이가 %d이고 평균은 %.2f입니다" % (stname, stage, stavg)) 
>>> print("{}학생은 나이가 {}이고 평균은 {:.2f}입니다".format(stname, stage, stavg)) 
>>> print(f"{stname}학생은 나이가 {stage}이고 평균은 {stavg:.2f}입니다")
```

* 변수 지정 시

```
>>> stname = "유니코"; stage=20; stavg=95.869
>>> v1 = stname+"학생은 나이가 "+str(stage)+"이고 평균은 "+str(stavg)+"입니다"
>>> v2 = "%s학생은 나이가 %d이고 평균은 %.2f입니다" % (stname, stage, stavg) 
>>> v3 = "{}학생은 나이가 {}이고 평균은 {:.2f}입니다".format(stname, stage, stavg) 
>>> v4 = f"{stname}학생은 나이가 {stage}이고 평균은 {stavg:.2f}입니다"
```



### 리스트

#### 자료의 집합

* 리스트는 여러 개 값을 집합적으로 저장
* 요소: 리스트에 소속되는 각각의 값, 주로 같은 타입 요소를 모음

* 대괄호에 첨자 지정 가능



#### 이중 리스트

> 리스트의 요소로 리스트 넣어 중첩 



#### list comprehension 지능형 리스트

#### :**`[값에 대한 수식 for 변수 in 대상 if 조건]`**



#### 삽입

* `append()`: 인수로 전달한 요소를 리스트 끝에 추가
* `insert()`: 삽입할 위치와 요소값을 전달받아 리스트 중간에 삽입
* 범위에 리스트 대입하여 여러 요소 한꺼번에 삽입 가능





#### 삭제

* `remove`: 인수로 전달받은 요소값 찾아 삭제
* `del`: 순서값 지정하여 삭제
* `clear`: 리스트 모든 요소 삭제
* 빈 리스트 대입: 일정 범위 요소 다수 삭제





#### 검색

* `index`: 특정 요소 위치 찾음
* `count`: 특정 요소 값의 개수 조사
* `in` / `not in`: 특정 요소 유무 여부 검사



#### 정렬

> 요소를 크기순으로 재배열

* `sort`: 리스트 정렬하며 요소 순서 조정, 리스트 자체 수정
* `reverse`: 요소 순서 반대로
* `key`: 정렬 시 요소 비교할 키 추출
* `sorted`: 원래 리스트 그대로 두고 정렬된 새로운 리스트 만들어 리턴





### 사전 

#### Dictionary

> 키와 값의 쌍을 저장하는 대용량 자료구조 **{}**

* 찾는 키가 없을 경우 예외 발생
  * 체크해서 찾기
  * 예외 처리 구문
  * `get` 메서드

* 특정 키 검색 시에는 `in` 구문 사용
* `del`: 해당 키를 찾아 값과 함께 삭제
* `dict_*객체`: 리스트처럼 순회하여 값 순서대로 읽음
* `update`: 두 개 사전 병합
* `dict()`: 빈 사전 만들거나 다른 자료형을 사전으로 변환



#### dictionary comprehension 지능형 사전

#### :**`{값에 대한 수식 for 변수 in 대상 if 조건}`**





### 집합

#### set()

> 빈 집합을 만들거나 다른 컬렉션을 집합형으로 변환



#### set comprehension 지능형 집합

#### :**`{값에 대한 수식 for 변수 in 대상 if 조건}`**

* `set()`: 공집합

* `add`: 집합에 원소 추가

* `update`: 합집합, 중복 허용X





### 

### 문자열 분리와 결합

#### Split

* 빈칸을 기준으로 문자열 분리
* ", "을 기준으로 문자열 나누기

* 리스트에 있는 각 값을 ~~변수로 언패킹
* ", "을 기준으로 문자열 나누기, 언패킹



#### Join

````
>>> colors = ['red', 'blue', 'green', 'yellow']
>>> result = "".join(colors)
>>> result
"redbluegreenyellow"
````





### 지능형 리스트

> 

#### 1. 조건 체크

```
# 리스트
[값 표현식 for 요소 in 입력Sequence]
[값 표현식 for 요소 in 입력Sequence if 조건식]
[값 표현식1 if 조건식 else 값 표현식2 for 요소 in 입력Sequence]
```

```
# 세트
{값 표현식 for 요소 in 입력Sequence}
{값 표현식 for 요소 in 입력Sequence if 조건식}
{값 표현식1 if 조건식 else 값 표현식2 for 요소 in 입력Sequence}
```

```
# 딕셔너리
{키 표현식: 값 표현식 for 요소 in 입력Sequence}
{키 표현식:값 표현식 for 요소 in 입력Sequence if 조건식}
{키 표현식:값 표현식1 if 조건식 else 값 표현식2 for 요소 in 입력Sequence}
```



* 리스트 예제

```
>>> result = [i if i % 2 == 0 else 10 for i in range(10)]
>>> result
[0,10,2,10,4,10,6,10,8,10]
```



#### 2. 중첩 반복문

> 리스트 2개를 섞어 사용 가능

```
>>> word1 = "Hello"
>>> word2 = "World"
>>> result = [i + j for i in word1 for j in word2]
>>> result
['HW','Ho','Hl', 'Hl', 'Ho', ...]

# word1에서 나오는 값을 먼저 고정한 후, word2의 값을 하나씩 가져와 결과 생성
```

```
# 필터링 적용
>>> case1 = ['A', 'B', 'C']
>>> case2 = ['D', 'E', 'F']
>>> result = [i + j for i in case1 for j in case2 if not(i==j)]
>>> result
['AD','AE','']
```



#### 3. 이차원 리스트

>대괄호 2개 사용
>
>기존 문장을 `split()`함수로 분리하여 리스트로 변환한 후, 각 단어의 대문자, 소문자, 길이를 하나의 리스트로 따로 저장

* 일차원 리스트 만드는 코드: 앞의 for문 먼저 실행

```
>>> [i + j for in case1 for j in case2]
```



* 이차원 리스트 만드는 코드: 뒤의 for문 먼저 실행

```
>>> [[i+f for i in case1] for j in case2]
```

