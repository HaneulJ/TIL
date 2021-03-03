## 3/3 수업

* API(Application Programming Interface): 자주 사용될 수 있는 기능들을 미리 만들어 놓은 프로그램
  * 어떠한 언어의API에 따라 함수, 클래스 등
  * R: 대부분 함수, 여러 함수들을 묶어 놓은 것 >> 패키지, 패키지 단위로 관리
  * 패키지 설치를 통해 필요한 함수들을 확장하여 사용 가능



### R 패키지

> R를 가지고 할 수 있는 통계, 분석, 시각화

* 새로운 R 패키지 설치: `install.packages("패키지명")`
* 이미 설치된 R 패키지 확인: `installed.packages()`
* 설치된 패키지 삭제: `remove.packages("패키지명")`
* 설치된 패키지의 버전 확인: `packageVersion("패키지명")`
* 설치된 패키지 업데이트: `update.packages("패키지명")`
* 설치된 패키지 로드: `library(패키지명)`, `require(패키지명)` 리턴값 有
* 로드된 패키지 해재: `detach("package:패키지명")`
* 로드된 패키지 점검: `search()`





#### 데이터 수집

* 웹 스크래핑: 웹 사이트 상에서 원하는 부분에 위치한 정보를 컴퓨터로 자동으로 추출하여 수집하는 기술
* 웹 크롤링: 자동화 봇인 웹 크롤러가 정해진 규칙에 따라 복수 개의 웹 페이지를 브라우징 하는 행위
* **CSS Selector**: 스크래핑하려는 페이지에서 원하는 태그 찾기
  * **XPath**





#### 정적 웹 페이지에 스크래핑에 사용되는 주요 API

* xml2 패키지 
  * `read_html(url)` : HTML 웹 페이지를 요청해서 받아오기
* rvest 패키지 
  * **`html_nodes(x, css, xpath)`**, `html_node(x, css, xpath)`: 원하는 노드(태그) 추출하기(여러개/하나만)
  * **`html_text(x, trim=FALSE)` : 노드에서 컨텐트 추출하기 **
  * `html_attrs(x)` : 노드에서 속성들 추출하기 
  * **`html_attr(x, name, default = "")` : 노드에서 주어진 명칭의 속성값 추출하기 **
* XML 패키지 
  * `htmlParse (file, encoding="…")` : `xpathSApply()` 사용 가능한 객체로 변환
  * ` xpathSApply(doc, path, fun)` : 원하는 노드(태그) 추출하고 전달된 함수 수행하기 
  * fun : xmlValue, xmlGetAttr, xmlAttrs
* httr 패키지 
  * GET(url) : HTML 웹 페이지를 요청해서 받아오기 
  * 요청헤더에 계정 또는 패스워드 등의 정보 전달 가능 
  * 응답 내용이 바이너리인 경우에도 사용 가능