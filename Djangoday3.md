## 1/28 수업

* `GET` 방식: url를 **직접** 입력해서 이동
* `POST` 방식: query 문자열 길이제한X, `{% csrf_token %}` 필수, `url 주소` **`/`** 

* `path('exercise10'/'<name>')`: < >변동 가능

* `forloop.`: Django 내장함수 중 하나



* https://docs.djangoproject.com/ko/3.1/

* 파이참 기능: `Alt`+`enter` 에러 해결책 안내

* **Spring FW**: 





##### 템플릿 태그

* `block` 및 ` extends`: 중복되는 html 파일 내용을 반복해서 작성해야 하는 번거로움 줄여줌

```
<!-- ~~~의 파일을 확장해서 사용하겠어-->
{% extends "~~~.html" %}
{% block title %}{{section title}}{% endblock %}
{% bock content %}
```



* `.getlist`: 정보 여러 개 선택 가능
* `info{ info1~~~}`: info안에 여러 객체 가능