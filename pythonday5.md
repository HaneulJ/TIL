## 1/8 수업

### 함수

#### 지역변수

> 함수 내부에서 선언하는 변수
>
> * 함수 내부에서만 사용되고 밖으로는 알려지지 않음



#### 전역변수

> 함수 바깥에서 선언하는 변수
>
> * 어디에서나 참조 할 수 있음

* l-value로 사용할 때 주의: **초기화하는 장소**에 따라 변수의 범위 결정

* **`global`** 변수명 : 전역변수로 사용할 것(지역변수가 있어도)

```
>>> price = 1000

>>> def sale():
    	global price        
    	price = 500         # 전역변수 price 의 값을 변경하게 된다.
    	print("sale", price) 

>>> sale()
>>> print("global", price)

sale 500
global 500
```

```
>>> def func1(p1, p2, p3, p4) :
    	global a, b, d
    	a = p1
    	b = p2
    	c = p3
   		d = p4
    	print('[지역] a=', a, ' b=', b, ' c=', c, ' d=', d, sep='', end='\n\n')

>>> a = 10
	b = 20
	c = 30
	print('[전역(함수호출전)] a=', a, ' b=', b, ' c=', c, sep='', end='\n')
	func1('A', 'B', 'C', 'D')
	print('[전역(함수호출후)] a=', a, ' b=', b, ' c=', c, ' d=', d, sep='', end='\n')


[전역(함수호출전)] a=10 b=20 c=30
[지역] a=A b=B c=C d=D
[전역(함수호출후)] a=A b=B c=30 d=D
```



#### Docstring 도큐먼트 주석

> 모듈 또는 함수의 첫번째 명령문으로 발생하는 문자 ilteral
>
> 함수 선언문`def`과 본체 사이에 작성

* `help()`

```
>>> help(print)
Help on built-in function print in module builtins:

print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream.
    
# keyword arguement:
# builtins:따로
```

* 함수 명명 후 바로 다음줄에 **""" """**로 표시

```
>>> def calcsum(n):
	""" 1~n까지의 합계를 구해 리턴한다."""
	sum = o
	for i in range(n+1):
		sum += i
	return sum
>>> print(calcsum(10))
>>> help(calcsum)

55
Help on function calcsum in module __main__:

calcsum(n)
    1 ~ n까지의 합계를 구해 리턴한다.
```



### 인수의 형식



#### arguement

* position arguement: 작성된 순서(위치)에 따라 매칭
* keyword arguement: 매개변수명=value, 순서 중요X

* 매개변수 **유무 & 갯수** 맞추기



#### 기본 값

> 잘 바뀌지 않는 인수는 인수 목록에 기본값 지정

* 기본값 매개변수: arguement가 없을 시에 함수가 정의될 때 같이 설정된 기본값 실행

```
# 기본값(디폴트) 매개변수
>>>def defaultfn1(p1=10, p2="abc", p3=True) :
   		print(p1)
    	print(p2)
    	print(p3)
    	print("=" * 10)

>>> defaultfn1(10,20,30)
>>> defaultfn1("abc", "xyz")
>>> defaultfn1(p2="가", p1="xyz", p3="P")
>>> defaultfn1()

10
20
30
==========
abc
xyz
True
==========
xyz
가
P
==========
10
abc
True
==========
```

```
# 일부 기본값(디폴트) 매개변수
>>> def defaultfn2(p1, p2="abc", p3=True) :
    	print(p1)
    	print(p2)
    	print(p3)
    	print("=" * 10)

# 이럴 땐 p1에 무조건 값이 있어야함.
```

* 앞쪽에 **키워드 인수**있으면 뒤쪽에 ***위치 인수 올 수 없음***



#### 가변인수

> 고정되지 않은 임의 개수의 인수를 받음

* *** 기호**

```
>>> def sumall(*p)
~~

>>> print(sumall(1,2,3,4,5))
>>> print(sumall(1,2,3))
# 다 가능
```









### 자료구조

> 정보(데이터)를 메모리에 효율적으로 저장하고 사용하는 방법
>
> 데이터 관리 방식
>
> 데이터 값의 모임, 데이터간의 관계, 데이터에 적용할 수 있는 함수로 구성

* 대용량일수록 메모리에 빨리 저장하고 빠르게 검색하여, 데이터를 효율적으로 사용하고 실행시간을 줄일 수 있게 해준다.
* 파이썬에서 지원하는 자료구조의 종류
  * 리스트: stack스택, queue 큐, tuple튜플
  * stack: 나중에 들어온 값을 먼저 나갈 수 있도록 해주는 자료구조 (last in first out)
  * queue: 먼저 들어온 겂을 먼저 나갈 수 있도록 해주는 자료구조(first i nfirst out)
  * tuple: 리스트와 같지만 데이터의 변경을 허용하지 않는 자료구조
  * set : 중복데이터 허용 X
  * dictionary 
  * collections 모듈: `len()`, `in`
* 컬렉션 
  * 시퀀스형(indexing, slicing, unpacking) : 문자열(불변), tuple(불변), list(가변)
    * indexing: 순서 지정
    * slicing: 범위 지정
    * unpacking
  * 집합형: set (가변)
  * 매핑형: dictionary (가변)

```
>>> "ABC" + "100"
"ABC100"		# 문자열은 불변형
```



#### Stack 스택

> Last in first out
>
> 마지막에 들어간 데이터가 가장 먼저 나오는 형태

* 데이터의 저장공간 구현
* push: 데이터 저장
* pop: 데이터 추출
* **리스트[]**라는 저장공간을 만든 후, `append()`함수로 데이터를 저장(push)하고 추출(pop)한다.

```
>>> a = [1,2,3,4,5]
>>> a.append(10)
>>> a
[1,2,3,4,5,10]
>>> a.append(20)
>>> a
[1,2,3,4,5,10,20]
>>> a.pop()
20					# 가장 마지막에 저장된 20이 추출
>>> a.pop()
10
```



#### Queue 큐

> first in first out
>
> 먼저 들어간 데이터가 먼저 나오는 형태

* `pop()`사용할 때 인덱스가 0번째인 값을 쓴다 = **`pop(0)`**

```
>>> a = [1,2,3,4,5]
>>> a.append(10)		# a = [1,2,3,4,5,10]
>>> a.append(20)		# a = [1,2,3,4,5,10,20]
>>> a.pop(0)
1						# 가장 맨 앞에 있는 1을 추출 
>>> a.pop(0)
2
```



### 컬렉션과 시퀀스

#### Sequence 시퀀스

> 정수로 indexing될수있는 유한한 길이의 순서가 있는 집합이며 slicing도 지원한다.

* `x in s; x not in s` 		# ;으로 두 문장 연결 
* s1 + s2
* indexing: `s[0]`, `s[1]`, `s[2]`, ... , `s[-1]`      # end 포함 x
* slicing: `s[i:j]`, `s[i:j:z]`
* packing과 unpacking: 개별 데이터로 시퀀스를 생성하고 시퀀스를 각각의 개별 데이터로 만드는 것
* 길이: `len(s)`
* 최소값: `min(s)`
* 최대값: `max(s)`                                 # 내장 함수
* 지정된 값의 개수: `s.count(x)`        # sequence만의 함수라 s.count()
* for문으로 순회하여 개별 문자 순서대로 꺼냄

```
>>> for d in [10,20,30]:
# sequence에 담겨있기 때문에 가능, 3회 실행
```



#### List 리스트 (=배열)

> 순서를 적용해서 여러 개의 데이터를 담는 상자

* 요소: 리스트의 각 데이터
* 각 요소는 순서에 따라 **인덱스**가 부여됨
* 하나의 리스트에 다양한 자료형의 데이터 저장 가능
* 주로 동일한 자료형으로 이루어진 항목을 순차적으로 추출하는 용도로 사용

```
>>> a = []
>>> b = list()

# a와 b의 결과 같음(비어있는 list)

>>> a = [being:end+1:increment]
# 슬라이싱

# 인덱싱의 경우: [~~~[--]~~~]
# 슬라이싱의 경우: [~~~--~~~]
```



##### 이차원 리스트

>리스트를 효율적으로 활용하기 위해 여러 개의 리스트를 하나의 변수에 할당

```
>>> kor_score = [49, 79, 20, 100, 80]
>>> math_score = [43, 59, 85, 30, 90]
>>> eng_score = [49, 79, 48, 60, 100]
>>> midterm_score = [kor_score, math_score, eng_score]


# print(midterm_score[행 인덱스][열 인덱스])
```



#### Tuple 튜플

>리스트와 유사하나 **읽기 전용**

* 속도가 빠름
* 튜플에서 제공되는 방법: `count`, `index`
* 튜플을 구성하는 각 요소 사이에 , 사용
* 하나의 요소로 튜플을 생성하려는 경우 요소 뒤에 **`,`**를 붙임 ex) (10,)
* `( , )`
* 적은메모리 공간 사용으로
* 함수의 인자들은 튜플로 전달
* 주로 서로 다른 종류의 데이터형의 항목을 변수에 바로 풀어쓰는 unpacking 혹은 색인을 매기는 용도로 사용

