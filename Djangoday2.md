## 1/27수업

```
http://localhost:8000/welcome/
http://localhost:8000/welcome/						firstapp.views.welcome
http://localhost:8000/secondapp/			views.exam1
http://localhost:8000/secondapp/exam2/		views.exam2
http://localhost:8000/secondapp/exam2_1/	
```



##### 가상환경_evev

> 하나의 PC에서 프로젝트 별로 독립된 파이썬 실행 환경(runtiome/interpreter)을 사용할 수 있도록 한다.

* 외부 패키지 설치 할 때: `pip`, 파이썬이 설치된 위치의 site-packages에



##### 장고 프로젝트 만들기

* 이동 명령 `cd c:\JHN\DJANGOexam`
* 프로젝트 생성: `django-admin startproject studyproject`
* `views`, `ulrs`, `settings` py 수정하기~
* `templates`는 직접 만들어서 `html`로 추가하기





* `HTTPRequest`: HTTP기반으로 요청이 왔을 때 요청 관련 정보 제공 객체, `view`함수가 호출될 때 아규먼트로 전달(장고서버가 객체 생성)
* `HTTPResponse`: HTTP기반으로 온 요청에 대한 응답시 사용하는 객체, 응답내용 담음(html태그문자열, 템플릿을 사용한 `render`객체)

ex) exam2

```
def exam2(request) :
    template = loader.get_template('exam2.html')
    if request.method == 'GET' :
        msg = "GET방식으로 했군요...ㅎ"
    else :
        msg = "POST방식으로 했군요...ㅎ"
    context = {'result' : msg}
    return HttpResponse(template.render(context, request))

// render(context를 template한테 전달, request도 전달)
// 기본: get 방식
```

ex) exam2_1

```
msg = request.GET.get("info1", "없음") + "-" + request.GET.get("info2", "없음") + "-" + request.GET.get("info3", "없음")

// url뒤에 query문자열에 info1로 전달된 값이 있으면 출력, 없으면 "없음"으로 출력
```

```
return HttpResponse(template.render(context, request))'''
return render(request, 'exam2_1.html', context)
// 동일
```





#### Query 문자열

> HTTP Client가 HTTP Server 요청시 서버에서 요청하려는 대상의 URL가 전달되는데 이 때 함께 전달될 수 있는 문자열

* `name=value`형식으로 구성
* 여러개의 `name=value` 사용시 **`&`**로 구분되게 구성
* 영문과 숫자: 그대로 전달
* 한글과 특수문자: **`%`**기호와 16진수 코드값으로 전달(UTF-8기준)
* 공백문자: **`+`** or **`%2C`** 로 전달
* Query문자열을 가지고 HTTP Server에게 정보를 요청할 때: **GET과 POST**
  * **`GET`**방식: 유사 dic, 문자열이 외부에 나타남, url 뒤에 `?`와 함께 전달
  * **`POST`**방식 일 때는 url에 **query 나타나지 않음** (로그인할 때), 반드시 `<form>`를 사용해야 `POST` 사용 가능, Query문자열 길이 제한X
* 







#### Django 템플릿

> 템플릿 변수: {{ 변수명 }}, 값 표현
>
> 템플릿 태그(로직): {% 로직 %}, 로직 구현

* dictionary로 전달! **{key : value}**
* 변수,  필터, 태그, 주석 등 제공
* `POST` 방식일 때 `<form> `안에 템플릿 태그가 필수: `{% csrf_token %}`
  * 보안을 위해서!

##### 템플릿 변수

> View에서 템플릿으로 객체 전달 가능

* `{{ 변수 }}`와 같이 사용





##### 템플릿 태그

* `{% tag %}` , `{% tag %} ... tag contents ... {% endtag %}` 

* `{% crsf_token %}`: `POST`방식, 보안 가능, `<form>` 전달값에 추가해야 함