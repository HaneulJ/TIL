## 1/7 수업

**git push 오류 시: `git pull origin master --allow-unrelated-histories`**

**Alt+Enter: 힌트**



### 1. 함수와 인수

#### 함수

> 어떤 일을 수행하는 코드의 코드블러 또는 코드의 묶음: 프로그램 재사용성

* 함수에 의해 처리되는 기능에 따라 데이터를 받을수도 있고 수행 결과 값을 return할 수 있다. 

  * 수행 결과값이 없는 경우에는 None이라는 literal이 return된다.
  * return값: 수행한 결과값을 되돌려주는 값
  * True, False 등

* 자주 반복되는 코드 사용이 용이해짐

* 호출문으로 실행: `print` `input`, `len`, `abs`(절대값)

* 장점

  * 필요할 때마다 호출 가능

  * 논리적인 단위로 분할 가능

  * 코드의 캡슐화

    

* 함수의 선언(정의)

```
>>> def 함수명(매개변수):	   #매개변수 정의는 선택사항, 개수제한X
		수행문1
		수행문2
		return <반환값>
```

* 함수이름

  * 소문자로 입력
  * 띄어쓰기 경우 _기호 사용
  * 행위기록 > 동사와 명사 함께 사용

  

* 함수 사용하는 방법(호출)

```
>>> 함수명()
>>>	함수명(값1, 값2)
```

* []: list만들 때 사용
* {}: dictionary
* (): 연산자 우선순위 조정, **함수호출 or 정의** > 함수(arguements..) 



#### 인수

> 호출할 때 함수로 전달되는 데이터

* **매개변수**를 통해 전달받음
* arguement(실인수): 함수를 호출하면서 전달하는 데이터ex) r-value

* 매개변수(형식인수): 함수 정의문의 인수, 아규먼트를 받아서 보관하는 변수, 함수가 호출될 때 전달받고자 하는 데이터를 저장하는 변수 ex) l-value
* arguement와 매개변수는 항상 함께
* 장점: 함수의 동작에 변활를 주어 활용성을 높임

```
>>> def calcsum(n):		  # n:매개변수, arguement를 받는 역할
		sum = 0
		for num on range(n+1):
			sum += num
		return sum
		
>>> print("~ 4=", clacsum(4))			# 4, 10:arguement
>>> print("~ 10=", clacsum(10))

~ 4 = 10
~ 10 = 55
```

```
>>> def calcrange(begin, end):	# 매개변수는 변수만 나열해도 됨
		sum = 0
		for num in range(begin, end + 1)
			sum += num
		return sum
		
>>> print("3~7 =", calcrange(3,7))
3~7 = 25
```



#### 리턴 값

> 함수의 실행 결과를 호출원으로 돌려주는 값

* 리턴 값을 반환할 때는 return명령 뒤에 반환할 값을 지정
  * 위의 clacsum함수의 경우: `return sum`

* 리턴값이 무조건 있어야 하는 것은 아님
* 리턴 값이 없는 함수는 리턴 값으로 `None`이 대신 리턴
* `print`함수는 return값 없음, 호출만 가능
* `input`함수는 return 값 있음, 호출 및 대입 가능





#### 예제

```
# temp: 지역변수, 함수 안에서만 사용 가능 <-> 전역변수, 함수 밖에서 사용 가능

>>> def kim():
    	temp = "김과장의 함수"		
    	print(temp)

>>> def lee():
    	temp = 2 ** 10
    	return temp

>>> def park(a):
   		temp = a * 2
    	print(temp)

>>> kim()
>>> print(lee())
>>> park(6)

김과장의 함수
1024
12

# print(temp)는 출력 불가: 지역변수, temp변수를 입력하지 않아서
```

```
>>> salerate = 0.9		# 전역변수

# 지역변수에 salerate가 없을 경우에는 전역변수를 가져다 씀
>>>>def kim():
    	print("오늘의 할인율 :", salerate)

>>> def lee():
    	price = 1000
    	print("가격 :", price * salerate)

>>> kim()				# 이 때 salerate = 0.9
>>> salerate = 1.1
>>> lee()				# 이 때 salerate = 1.1
################
>>> price = 1000

>>> def sale():
    	price = 500		# price: 지역변수
    					# 이 함수 안에서만 price=500
>>> sale()
>>> print(price)

오늘의 할인율 : 0.9
가격 : 1100.0
1000
```

