## 2/3 수업

* 페이징: 게시판 글의 리스트를 분할해서 보여주기(Django에 내장)



#### 리스트 페이징







#### Django의 relationships

> 테이블 간의 관계 설정



##### 다대일 관계

> 한 테이블에 있는 두 개 이상의 레코드가 다른 테이블에 있는 하나의 레코드를 참조

* Order 테이블의 customers테이블의 기본키인 ID필드를 참조
  * Order테이블의 Customer_ID필드: 외래키 필드
* 외래키: 다대일 관계 설정할 때 사용
  * 모델 클래스의 속성으로 입력
  * 연결대상이 될 모델 객체를 위해 위치인자로 전달
  * `on_delete`옵션 필수 입력

```
class 모델이름(models.Model):
	필드이름 = models.ForeignKey(연결대상모델,on_delete=삭제옵션)
```

```
# customer table
class Customer(models.Model):
	customer = models.ForeighKey(Customer,on_delete=models.CASCADE)
	productname = models.CharField(max_length=50)

# 테이블 생성 시 해당 컬럼에는 _id 가 붙는다
```



* ForeignKey 필드의 이름

  : 



* `on_delete` 옵션

  :





#### redirect와 render







* `display:none` 화면에 보이지 마
  * `block` 
* 새로고침 역할: `location.href = "{% url 'vR' %}?page="+{{ vlist.number }`







#### Django 인증 시스템

* 로그인 기능과 로그아웃 기능 지원하는 앱과 프로그램 내장



* 관련 API

```
from django.contrib
import auth
from django.contrib.auth.models import User
```

* 회원 가입

```
User.objects.create_user(
회원정보를 키워드 아규먼트로 설 정
user = User.objects.create_user(username = useremail,
first_name = firstname,
last_name = la stname,
password = password)
```

* 회원 체크

```
auth.authenticate(username=
사용자계정 , 사용자패스워드
(
리턴 값
회원이
아니면 None
회원이면
해당 회원의 User 객체
```

* 로그인: `auth.login(request, User)`
* 로그아웃: `auth.logout(request)`
* 로그인 여부 체크: `request.user.is_authenticated`