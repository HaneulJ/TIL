## 1/13 수업

### 컬렉션 관리함수

#### enumerate

> 순서값과 요소값을 한꺼번에 구하는 내장함수

* 예시: 여러 학생의 성적 출력

```
>>> score = [88,95,70,100,99]
>>> for no, s in enumerate(score,1):
		print(str(no)+ "번 학생의 성적:", s)

# index를 사용한 방법
>>> for no in range(len(score)):
		print(str(no + 1) + "번 학생의 성적:", score[no])
```

* `enumerate`안에는 tuple이 들어있다!



```
# 딕셔너리 컴프리헨션 예제
>>> {i:j for i, j in enumerate("TEAMLAB is an acdemic institute located in South Korea.".split())}
{0:'TEAMLAB', 1: 'is', 2: 'an', 3: 'acdemic', 4: 'institute', 5: 'located', 6: 'in', 7: 'South', 8: 'Korea'}
```



#### zip

> 여러 개 컬렉션 합쳐 하나로 만듬

* 두 리스트의 대응되는 요소끼리 짝지어 **튜플 리스트** 생성
* 1회성!
* 합쳐지는 두 리스트의 길이는 무관
* 생성되는 튜플의 순서는 원본 리스트와 같음







### 파이썬의 함수는

##### 1. 변수에 저장 가능

##### 2. 함수를 담고 있는 변수를 통해서 함수 호출 가능

##### 3. 다른 함수 호출 시 아규먼트로 전달 가능

##### 4. 함수의 리턴 값으로 전달 가능

##### 5. 일반적인 데이터처럼 사용 가능





#### filter

> 리스트 요소 중 조건에 맞는 것만 골라냄

* 첫번째 인수: 조건 지정하는 **함수**
* 두번째 인수: 대상 리스트

```
>>> def flunk(s):
		return s < 60
>>> score = [45,89,72,53,94]
>>> for s in filter(flunk, score):
		print(s)
45
53
# flunk(): 점수 s를 인수로 받아 60 미만인지 조사
# True인 값만 출력
```



#### map

> 모든 요소에 대한 변환함수 호출, 새 요소 값으로 구성된 리스트 생성

* 첫번째 요소 : 값을 변환하는 함수
* 두번째 요소: 대상 리스트
  
  

```
>>> def half(s):
		return s/2
>>> score = [45,89,72,53,94]
>>> for s in map(half, score):
		print(s, end=", ")
22.5, 44.5, 36.0, 26.5, 47.0

# half(): 인수로 전달 받은 s를 절반으로 나누어 리턴
```



### 람다 함수

> 이름 없고 입력과 출력만으로 함수를 정의하는 축약된 방법

#### `lambda 인수:식`

* 인수: 호출 시 전달받을 아규먼트(생략 가능), 여러 개 가능
* 식: 호출 시 전달할 리턴 값 

```
>>> score = [45,89,72,53,94]
>>> for s in filter(lambda x:x < 60, score):
		print(s)
45
53
```

* **lambda arguments : expression**

* 람다 함수 내에서는 변수 정의 불가
* 람다 함수 내에서는 식만 정의 가능





### 컬렉션의 사본

#### 리스트의 사본

* 기본형 변수는 대입 이후 둘 중 하나 바꾸어도 다른 쪽에 영향X
* 컬렉션의 경우, 같은 리스트를 두 변수가 가리키는 것이라 영향O

```
>>> a = 3
>>> b = a
>>> print("a = %d, b = %d" % (a,b))

>>> a = 5
>>> print("a = %d, b = %d" %(a, b))
a = 3, b = 3
a = 5, b = 3

# 다름
>>> list1 = [1, 2, 3]
>>> list2 = list1

>>> list2[1]=100
>>> print(list1)
>>> print(list2)
[1, 100, 3]
[1, 100, 3]
```

* `copy`로 두 리스트를 완전히 독립 사본으로 만들 수 있음

```
>>> list1 = [1,2,3]
>>> list2 = list1.copy()

>>> list2[1] = 100
>>> print(list1)
>>> print(list2)
[1, 2, 3]
[1, 100, 3]
```

```
>>> list0 = ['a', 'b']
>>> list1 = [ list0, 1, 2]
>>> list2 = list1.copy()

>>> list2[0][1] = 'c'
>>> print(list1)
>>> print(list2)
[['a', 'c'], 1, 2]
[['a', 'c'], 1, 2]
```

* `deepcopy`: copy 모듈이 가지고 있는 추가적인 함수(`import copy`), sub 리스트까지 복제 가능

```
>>> import copy

>>> list0 = ['a', 'b']
>>> list1 = [list0, 1, 2]
>>> list2 = copy.deepcopy(list1)

>>> list2[0][1] = 'c'
>>> print(list1)
>>> print(list2)
[['a','b'], 1, 2]
[['a','c'], 1, 2]
```





#### is 연산자

> is 구문을 통해 두 변수가 같은 객체 가리키는지 조사

* 대입에 의한 같은 변수: 동일한 id 값
* copy에 의한 독립적인 사본: 다른 id 값

```
# 대입에 의한 변수는 True
# copy에 의한 변수는 독립적인 사본 False
>>> list1 = [1, 2, 3]
>>> list2 = list1
>>> list3 = list.copy()

>>> print("1==2", list1 is list2)
>>> print("1==3", list1 is list3)
>>> print("2==3", list2 is list3)
1 == 2 True
1 == 3 False
2 == 3 False
```







### 리스트의 메모리 관리 방식

#### 리스트의 메모리 저장

* `==`: 값을 비교
* `is`: 메모리 주소를 비교

```
>>> a = 300
>>> b = 300
>>> a is b
False
>>> a == b
True
```

* 파이썬은 **-5 ~ 256 정수값을 특정 메모리 주소에 저장**: `is` & `==` True
* 해당 숫자를 하려고 하면 해당 변수는 그 숫자가 가진 메모리 주소로 연결한다.



* 파이썬은 리스트를 저장할 때 값 자체가 아니라, 값이 위치한 메모리 주소(reference)를 저장한다.
* 리스트: 값이 있는 주소 저장(값을 연속으로 저장 X)





### 표준 모듈 사용

#### 모듈

> 파이썬 코드를 저장하는 기본 단위
>
> R에서는 '패키지' 라 불림

* 파이썬 소스 파일 (.py)
* `import 모듈명 [as 별칭]`
* `from 모듈 import 함수명 [as 별칭][,함수명[as 별칭]]`

* `from 모듈 import 함수명`

```
>>> from mate import sqrt
>>> print(sqrt(2))

# sqrt외의 math에 속한 다른 함수는 사용 불가
```





### 시간

#### Epoch 시간 = 유닉스 시간

> 날짜와 시간 관련 기능 제공

* `time` 모듈

```
>>> import time
>>> time.time()
>>> print(time.ctime(t))
Wed Jan 10 10:58:24 2019
```

* `localtime` 함수
  * 지역 시간 고려하여 현지 시간 구함
  * 시간 요소 멤버로 가지는 strut_time형 객체로 반환
  * 정보 분리하여 문자열로 조립

* 실행 시간 측정

  : time 함수 호출 시점에 따라 구해지는 시간이 다름을 이용



#### calendar 모듈

* `month`
* `weekday`

* `calendar`



#### random 모듈

> 난수 생성 기능

* `random`
* `randint(begin, end)`: 
* `randrange(begin, end)`: end 제외

* `shuffle`
* `choice`
* `sample`: 리스트에서 n개 를 무작위로 뽑아 리스트 만듦