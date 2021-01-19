## 1/19 수업

* 실습 리뷰

```
# f를 정의해줘야 함
>>> f = None
```

```
# f를 먼저 써줘야 문자열안에 있는 {}들이 실행된다.
>>> f.write(f"오늘은 {now.tm_year}년 {now.tm_mon:02d}월 {now.tm_mday:02d}일입니다.")
```

```
# close는 필수
# with as절은 close 자동 포함
>>> if f:
		f.close()
```

```
# month와 prmonth의 차이점
>>> calendar.month
>>> calendar.prmonth
# prmonth는 print를 쓰지 않아도 출력이 됌
```





### OOP(Object Oriented Programming)

#### 객체 지향 프로그래밍이란

> 객체 안에 관련된 변수와 함수를 정의하여 객체 단위로 기능이 처리되도록 하는 프로그래밍 기법

* **재사용성, 확장성**
* 소프트웨어 개발과 유지보수 간편, 직관적인 코드 분석 가능

* 인스턴스화: 클래스를 메모리 할당 해서 해당 객체 초기화

* 추상화: 만들고자 하는 프로그램에서 어떤 객체가 필요하면 먼저 그 객체의 멤버들을 모델링(추상화)하여 클래스를 정의
* 파이썬!!
  * 개발하려는 시스템 또는 프로그램에서 어떤 역할이 필요
  * 그 역할을 제공하는 객체를 생성
  * 객체를 만들려면 객체의 구조를 정의한 클래스 필요
  * API로 제공되는 경우 or 이전에 만들어져 있는 상황 > 객체 생성, 사용
  * 그렇지 않은 경우 > 객체를 모델링하고 클래스로 구현한 후 객체 생성
* 클래스 정의 방법

```
class UserInfo:
	변수정의
	변수정의
```

* 객체 생성 방법

```
변수 = 클래스명()
```

* 객체 사용 방법

```
변수.변수명
변수.메서드명()
```

* 객체 초기화 method `init` / 소멸 method `del`

```
class Student:
	def __init__(self):
		print("인스턴스 생성")
   
	def __del__(self):
		print("인스턴스 삭제")
     
st1 = Student()			
st2 = Student()
st3 = Student()

print("st1이 참조하고 있는 Student 인스턴스 삭제")
del st1

# self: 매개변수 최소 1개 이상, 참조값을 첫 번째 아규먼트로 무조건 전달
		이름 변경 가능
```

* 예시

```
class Student :
   '''
   학생 객체를 생성할 수 있는 Student 클래스입니다.
   인스턴스 생성시에는 학생의 이름, 나이, 과목명을 전달하세요.
   '''
# docstoring

   def __init__(self, name, age, subject):
       self.name = name
       self.age = age
       self.subject = subject
# 객체만의 변수(=member 변수) 만듦: 초기화 method

   def printStudentInfo(self):
       print("{}의 나이는 {}세입니다.".format(self.name, self.age))

   def study(self):
       print("{} 학생은 {} 과목을 학습합니다.".format(self.name, self.subject))

st1 = Student("둘리", 10, "파이썬")
st2 = Student("도우너", 12, "자바")
st3 = Student("또치", 10, "자바스크립트")
```



#### 파이썬 객체지향 구문의 특성

* 클래스 정의, 다중상속, 연산자 오버로딩 지원
* 클래스: 속성과 동작을 하나의 범주로 묶어 실세계의 사물을 프로그램 코드로 흉내
* 모델링: 사물을 분석하여 필요한 속성과 동작 추출
* 캡슐화: 모델링한 결과를 클래스로 포장





#### 클래스

> 관련된 속성과 동작을 하나의 범주로 묶어 실 세계의 사물을 흉내 냄

* 객체 개념 적용한 프로그램
  * method: `deposit`, `inquire`
  * 변수: name, balance

```
>>> class Account:
		def __init__(self,name,balance):
			self.name = name
			self.balance = balance
			
		def deposit(self, money):
			self.balance += money
		
		def inquire(self):
			print("%s의 잔액은 %s원입니다." % (self.name, format(self.balance, ',')))
			
>>> obj1 = Account("둘리", 8000) 
>>> obj2 = Account("또치", 8000) 
>>> obj3 = Account("도우너", 8000)
```

* 멤버: 클래스 구성하는 변수와 함수
* 메서드: 클래스에 소속된 함수
* 인스턴스: 특정 객체가 어떤 클래스의 객체인지를 *관계* 위주로 설명할 때 사용
  * `a=Cookie()`: a는 객체다, a객체는 Cookie클래스의 인스턴스이다.



#### 생성자

```
>>> class 이름:
		def __init__(self, 초기값):
			멤버 초기화
		메서드 정의
# 초기값: 주로 멤버 변수의 초기값
```



#### 객체 생성 구문

>  `객체 = 클래스명(인수)`

* 예제: `obj1 = Account(“둘리”, 10)`

```
>>> def __init__(self, name, balance): 
		self.name = name 
		self.balance = balance
```

1. Account 클래스 메모리 할당(Account 클래스 객체 생성)
2. 할당된 주소는 생성자의 첫 번째 매개변수인 self 에게 전달되고 나머지 아규먼트들은 그 다음 매개변수들에게 전달된다.
3. 초기화 메서드에서는 Account 클래스가 할당된 메모리 영역에 name과 balance 변수의 방을 만들고 각각 매개변수의 값을 대입하여 초기화하면 객체 생성 과정은 완료된다.
4. 생성 완료된 객체의 참조값을 obj1에 대입한다. 이제부턴 이 객체를 **obj1 객체**라 부른다.



* 초기화 메서드 외에 다른 일반 메서드는 객체를 통해서 호출 가능함: `객체.메서드()`



* `init`: 호출이 없는 경우(내부적으로 자동 생성)

```
>>> class FourCal:
		def setdata(self, first, second):
			self.first = first
			self.second = second
			
>>> a = FourCal() 
>>> a.setdata(4, 2)

# a = FourCal()로 빈 함수 호출
```



#### 상속

> 기존 클래스 확장하여 멤버 추가하거나 동작 변경

`class 이름(부모)`

*  `super().__init__()`: 자식 클래스에서 부모의 초기화 메서드를 호출할 때 사용
*  `class 자식클래스명(부모1, 부모2)`: 부모 클래스를 2개 이상 지정 가능
   * 우선순위: 부모1-부모2





#### 클래스 변수와 인스턴스 변수

```
>>> class Test:
		클래스 변수
		인스턴스 변수
```

* 클래스 변수에 대한 접근: `Test.클래스 변수`, `o1.클래스 변수`, `o2.클래스 변수`
* 인스턴스 변수에 대한 접근: `o1.인스턴스 변수`, `o2.인스턴스 변수`

```
>>>class Book:
		sale = "yes24"
    	def __init__(self,title,author,price):
        	self.title = title
        	self.author = author
        	self.price = price
# sale: 클래스 변수
# self.title: 인스턴스 변수
```

