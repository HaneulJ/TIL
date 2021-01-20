## 1/20 수업 (1)_Python

### 여러가지 메서드

#### 클래스 메서드

> 클래스 전체에 공유, 객체를 통해 호출
>
> `@classmethod` 데커레이터 사용

* 첫 번째 인수로 클래스에 해당하는 `cls` 인수 정의



#### 정적 메서드

> 클래스에 포함되는 단순 유틸리티 메서드
>
> `@staticmethod` 데커레이터 사용

```
>>> class 클래스명(부모클래스명):
		def m1(self):
			pass
			@classmethod
		def m2(cls):			# 클래스메서드가 호출될 때 cls에 class에 대한 정보가 전달
			@staticmethod	
        def m3():				
        	pass
#():stasticmethod는 아무것도 전달X, 클래스 안에 있어야 하지만 단독으로 수행되는 게 맞을 때(다른 멤버들과는 관련x)
```



#### 연산자 메서드

> 연산자를 사용하여 객체끼리 연산

* 연산자 오버로딩: 클래스별로 연산자 동작을 고유하게 정의



#### 특수 메서드

> 특정한 구문에 객체 사용될 경우 미리 약속된 작업 수행





### 모듈

#### 모듈 작성 및 사용

> 파이썬 코드를 저장하는 기본 단위

* `dir`: 모듈이 가지고 있는 목록 리스트 형식으로 표시
* `cd`: 디렉토리 옮기기

```
test1.py
	def f1():
		pass
	def f2():
		pass
	f1()
	f2()
# 호출 개수 제한 X

test2.py
	def f1():
		pass
	f1()
# test2의 f1이 호출

# test1을 가져와 사용할 때, test2가 주연
test2.py
	import test1
	def f1():
		pass
	f1()
	test.f1()
	
# 모듈명을 main으로 바꿀 때? 함수만 실행되고 f1,f2,f3는 실행X (단독으로 수행될 때만 실행됌, import될 때는 X)
test1.py
	def f1():
		pass
	def f2():
		pass
	if __name__=="__main__"
		f1()
		f2()
		f3()
```



#### 테스트 코드

> 모듈에 간단한 테스트 코드 작성 가능





#### 모듈경로

* 모듈은 임포트하는 파일과 같은 디렉토리에 있어야함
* 특정 폴더에 두려면 임포트 패스에 추가

```
>>> import sys
>>> sys.path.append("C:/PyStudy")
>>> print(sys.path)
>>> import mypack.calc.add
>>> mypack.calc.add.outadd(1,2)
# mypack 폴더 -> calc폴더 -> add.py파일 을 import해서 내보내겠다~(out 이용)

>>> import mypack.calc.add as my1
>>> my1.outadd(1,2)
# 가능
```





### 패키지

> 모듈을 담는 디렉토리

`from 패키지 import 모듈`

`import.패키지...모듈`

* 디렉토리로 계층 구성하면 모듈을 기능 등에 따라 분류 가능
* sub 모듈도 표시해줘야함



#### `__init__.py`

> 모든 모듈 한꺼번에 불러올 때는 어떤 모듈 대상인지 밝히기
>
> 임포트할 대상 모듈 리스트 명시

* 전체를 `*`import할 패키지 안에 `__init__.py`가 있어야 사용가능

```
>>> from mypack.calc import *
>>> add.outadd(1,2)
>>> multi.outmulti(1,2)
```

