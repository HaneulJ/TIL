## 1/26 수업

cloud.google.com/maps/official

* ggmap 예제4: 현재 위치 표시

```
navigator.geolocation.getCurrentPosition(function(position) {
					var latlng = { lat: position.coords.latitude, lng: position.coords.longitude }
					var map = new google.maps.Map(dom, {
			           	center: latlng,
			           	zoom: 16
			       	}
```



### [DJango]

#### 웹의 기본 이해

> WWW, 인터넷이라는 연결을 통해 여러 컴퓨터가 연결되어 서로 정보를 나누는 연결망

* 서버: 정보를 제공하기 위해 고정된 주소, 방문하는 컴퓨터들에게 필요한 정보 제공

* 클라이언트: 정보를 제공받기 위해 서버를 찾아 접속하는 컴퓨터,  고정된 주소 없이 인터넷 연결을 통해 접근(웹 브라우징)
* 요청-응답-통신



##### 웹프로그램의 구조별 개념

* 프론트앤드: 사용자들이 화면의 모습 결정, HTML, CSS, JavaScript
* 백엔드: 사용자가 접속하면 그에 맞는 데이터를 보내주기 위해 여러가지 처리, Django기반의 프로그래밍이나 DB(CGI/PHP/Servlet/JSP/NodeJS/SprintMVC)



##### 서버-클라이언트 간 통신 방향 별 개념 

* 요청: 클라이언트가 서버로 원하는 정보를 받기위해 필요한 정보를 보내는 과정, 브라우저 프로그램이나 모바일 여부 / URL

* 응답: 요청을 받은 서버가 받은 데이터를 처리하여 사용자에게 정보를 내려 주는 것, HTML, CSS, JavaScript코드를 웹 브라우저가 해석하고 실행(JSON, XML)



#### HTTP 프로토콜(통신규약)

> Hypertext Transfer 통신 프로토콜, 상호 간에 정의한 규칙



##### HTTP 프로토콜의 특징

* stateless 프로토콜: 접속상태 유지X
* 다수의 요청 처리 및 서버의 부하를 줄일 수 있음
* 기본 포트: **80** (8000)



##### HTTP Request & Response

* 데이터를 주고받기 위해 요청을 보내고 응답을 받아야 함
* request(클라이언트) - response(서버)



##### URL

* 서버에 자원을 요청하기 위해 입력하는 영문 주소
* 구조: **protocol :// host(ip주소): port / resource path ? query**
  * resource path 생략: 기본파일로 달라(index.html)



##### HTTP 요청 메서드

* 요청하는 데이터에 특정 동작을 수행하고 싶을 때 이용
* get: 존재하는 자원에 대한 요청(기본 요청 방식)
* post: 새로운 자원을 생성



##### HTTP 상태 코드

* 2xx: 성공   ex) 200
* 3xx: 리다이렉션
* 4xx: 클라이언트 에러  ex) 404
* 5xx: 서버 에러  ex) 500





#### Django

> 파이썬으로 작성된 오픈 소스 웹 서버 애플리케이션 프레임워크
>
> 모델-뷰-컨트롤러 패턴

* https://www.djangoproject.com/

* 목표: 수월한 DB기반 웹사이트 작성

* ex) instagram, pinterest





##### 장고 프로그램의 개발 패턴

> MVC(Model View Controller) 패턴

* Model = **Model**: DB 동작
* View = **Template** : 사용자에게 보여지는 영역
* Controller = **View** : 실직적으로 프로그램 로직이 동작하여 적절한 처리결과를 Template에게 전달(중간관리자)
* 요청 로직과 응답 로직으로 나누어 개발
  * 요청 로직: Controller
  * 응답 로직: View
* 처리데이터는 Model로 개발, 확장성과 유지보수성 향상



##### 장고의 처리 흐름

* 웹 클라이언트의 요청을 받아 장고에서 MTV 모델에 따라 처리하는 과정

  * 클라이언트로부터 요청을 받으면 URLconf 모듈을 이용하여 URL 분석

    ```
    urlpatterns = [
    path('welcome/', firstapp.views.welcome),
    ]
    ```

  * URL 분석 결과를 통해 해당 URL에 매칭되는 뷰 실행

  * 뷰는 자신의 로직 실행, 데이터 베이스 처리가 필요하면 모델을 통해 처리하고 그 결과를 받환 받음

    ```
    from django.http import HttpResponse
    def welcome(request):
        return HttpResponse("<h1>장고 공부를 재미있게 합시다!!</h1>")
    ```

  * 뷰는 자신의 로직 처리가 끝나면 템플릿을 사용하여  클라이언트에 전송할 HTML파일 생성

  * 뷰는 최종 결과로 HTML파일을 클라이언트에게 보내 응답



##### 장고 코드

* 새 폴더 만들 때`python manage.py 폴더명 ~~~` 
* 실행 시 `python manage.py runserver` 
* 실행 취소시 `ctrl + c`
* 웹에서 확인: `http://localhost:8000/폴더명/`

* 전역 링크 - 지역 링크

```
path('secondapp/',include('secondapp.urls'))
를 지정하면 secondapp의 url에서~

second view에서
path('', views.exam1, name='exam1')
" "라는 아무것도 입력하지 않으면 exam1을 내보낸다.
```

* 템플릿 지정 방법

```
def exam1(request):
    template = loader.get_template('exam1.html')
    return HttpResponse(template.render(None, request))
```

* `{{ }}`: 변수
* `{% %}`



##### Views와 Templates

* `urls.py`: 프로젝트 폴더(메인)과 앱폴더(서브)
* `views.py`: 앱폴더
* `templates\xxx.html`: 앱폴더





#### 라이브러리와 프레임워크

##### 라이브러리(API)

> 재사용이 필요한 기능으로 반복적인 코드 작성을 없애기 위해 언제든지 필요한 곳에서 호출하여 사용할 수 있도록 함수로 만들어짐

* 사용여부: 코드 작성자 선택 사항
* 프로그램 제작시 필요한 기능



##### 프레임워크

> 원하는 기능 구현에만 집중하여 빠르게 개발할 수 있도록 기본적으로 필요한 기능을 갖추고 있는 것

* 라이브러리 포함
* 프레임워크로만 실행X
* 기능 추가, 프레임워크에 의존하여 개발
* 프레임 워크가 정의한 규칙 준수

* 프로그램 기본 구조(뼈대)