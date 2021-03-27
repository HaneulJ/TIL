## 3/25 수업



### urllib 패키지를 활용한 웹페이지 요청

> 파이썬 표준 라이브러리

#### [urllib request]

* url문자열로 HTTP요청 수행
* `urlopen()`으로 웹서버에 페이지 요청, 서버로부터 받은 응답 저장, 응답객체 반환
* `res = urllib.request.urlopen("요청하려는 페이지의 url 문자열")`



##### http.client.HTTPResponse클래스bb

* 응답 헤더나 응답 바디의 내용을 추출하는 메서드 제공
* `HTTPResponse.read([amt])`

* `HTTPResponse.getheaders()`



* ` get_content_charset()`: 응답내용이 어떤 캐릭터셋으로 만들어진 것인지 파악



#### [urllib.parse]

> 웹 서버에 페이지 또는 정보를 요청할 때 함께 전달하는 데이터

* GET 방식: Query 문자열
* POST 방식: 요청 파라미터

* `name=value&name=value&name=value&...`
* 영문과 숫자는 그대로 전달
* 한글은 %기호와 함께 16진수 코드 값으로 전달



* `urllib.parse.urlparse()`: 아규먼트에 지정된 url문자열의 정보를 **urllib.parse.ParseResult**객체로 리턴
* `urllib.parse.urlencode()` : 메서드의 아규먼트로 지정된 name과 value로 구성된 딕셔너리 정보를 정해진 규격의 Query 문자열 / 요청 파라미터 문자열로 리턴



* GET방식: Query문자열을 포함하여 요청 
  * url뒤에 `?` 추가하여 요청url로 사용

* POST방식:  요청 바디안에 요청파라미터를 포함하여 요청
  * `encode('ascii')` 메서드 호출하여 바이트 형식의 문자열로 변경
  * `urllib.request.urlopen()` 호출 시 바이트 형식의 문자열로 변경된 데이터를 두 번째 아규먼트로 지정 







### requests 패키지를 활용한 웹 페이지 요청

> HTTP프로토콜과 관련된 기능 지원

* `conda install requests` / `pip install requests`로 설치
* 





#### requests.request()함수

> HTTP 요청을 서버에 보내고 응답을 받아오는 기능 지원

* 딕셔너리 형태로 데이터 전송
* ` request()`함수 호출 시 요청 메서드(GET, POST)를 명시하여 요청



* `requests.request(method, url, **kwargs)` : 가변키워드 아규먼트
  * method: 요청방식 지정(GET, POST, ...)
  * url: 요청할 대상 URL 문자열 지정
  * params: [선택적] 요청 시 전달할 Query 문자열 지정(딕셔너리, 튜플리스트, 바이트열 가능)
  *  data: [선택적] 요청시 바디에 담아서 전달할 요청 파라미터 지정(딕셔너리, 튜플리스트, 바이트열 가능)

* `requests.request()` 함수에 요청방식을 지정하여 호출하는 것과 동일
  * `requests.get(url, data=  , json=  , **kwargs)`



* **GET** 방식 요청

  * `requests.request('GET',url, **kwargs)`

  * `requests.get(url, params=None, **kwargs)`

* **POST** 방식 요청

  * `requests.request('POST', url, **kwargs)`
  * `requests.post(url, params=None, **kwargs)`



* `requests.request()`, `requests.get()`, `requests.head()`, `requests.post()`함수의 리턴값은 모두 **`requests.models.Response`**
  * Text: 문자열 형식, `r.encoding = 'utf-8'`로 설정한 후 추출
  * Content: 바이트열 형식, `r.content.decode('uft-8')`





#### [HTTP Response]

* Header: 응답상태코드, 응답메세지
  * name: value로 구성되는 여러 정보들
* Body: HTML 전체 내용