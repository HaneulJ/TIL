## 2/1 수업_[Django]

### Django 모델

> 데이터 서비스 제공
>
> `models.py`에서 정의

* 모듈 안에 하나 이상의 **모델 클래스** 정의 가능
* 하나의 모델 클래스는 데이터베이스에서 하나의 테이블에 해당
* ORM 기술: 모델클래스(객체 Object)-데이터베이스 테이블(Relation) Mapping

* Django모델: `django.db.models.Model`의 자식 클래스
  * 모델의 필드(필수): 클래스의 속성, 테이블의 컬럼, 모델 API와 동일한 이름으로 생성하지 않도록 주의
  * 기본키 지정안될 시: 모델에 기본키 역할을 하는 id필드 자동 추가
  * DB 테이블 생성 시 자동으로 값이 1씩 증가하는 id 컬럼 생성

```
class 모델 이름(models.Model):
	필드이름1= models.필드타입(필드 옵션)
	필드이름2= models.필드타입(필드 옵션)
```

* 모델클래스에 필드 정의할 때는 **클래스 변수**로 정의
* 변수에는 테이블의 컬럼의 메타 데이터를 정의
* `models.CharField()`: 
* `models.IntegerField()`
* `models.DateTimeField()`
* `models.TextField()`





#### CRUD(Creat Read Update Delete)

* SQL: insert, select, update, delete
* Dajngo API (python)



##### Django를 가지고 Database를 연동(CRUD)하는 구현 과정

1. 모델 클래스 생성

   : `models.py`에, Model이라는 클래스를 상속, 만들려는 DB테이블 컬럼 사양에 맞춰 클래스 변수 정의

2. Django에서 제공하는 명령을 수행시켜 모델클래스에 알맞는 DB테이블 생성

3. 모델클래스를 통해서 CRUD 구현

   * C: 모델클래스 객체 생성 후 `save()` 메서드 호출

   * R

     ```
     모델클래스.objects.all()
     모델클래스.objects.filter(...)
     모델클래스.objects.order_by(..)
     모델클래스.objects.first()
     모델클래스.objects.last()
     모델클래스.objects.count()`
     ```

     