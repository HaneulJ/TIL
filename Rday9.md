## 3/5 수업

### 동적 웹페이지 크롤링(스크래핑)

* 서버로부터 보내진 웹페이지에 내용이 없으면 정적 X
  * "페이지 소스" 에서 안보임
  * "개발자도구" 소스: 렌더링이 끝난 소스(각종 자바스크립트 코드들이 같이 수행된 상황)

* Selenium: 웹사이트의 테스트를 자동화해주는 서버, 동적페이지에 대한 크롤링과 스크래핑을 원할하게 할 수 있음~(Java 기반)



```
# R 코드로 Selenium 서버에 접속하고
remoteDriver 객체 리턴
remDr <- remoteDriver(remoteServerAddr="localhost",
port=4445,browserName="chrome")

# 브라우저 오픈(크롬)
remDr$open()

# url 에 해당하는 웹페이지 랜더링
remDr$navigate(url)

# 태그 한 개 찾기(webElement 객체), 태그가 없으면 NoSuchElement 오류 발생
one <- remDr$findElement(using='css selector',‘css선택자')

# 찾아진 태그의 태그 명 추출
one$getElementTagName()

# 찾아진 태그의 태그 내용 추출
one$getElementText()

# 찾아진 태그의 속성 명에 대한 값 추출
one$getElementAttribute(”속성명”)

# 찾아진 태그에서 클릭이벤트 발생시키기
one$clickElement()

# 태그들을 찾기, 존재하지 않으면 비어있는 리스트 리턴
# 찾은 태그의 갯수만큼의 rem엘먼트 객체들의 리스트
doms <- remDr$findElements(using ="css selector","컨텐트를추출하려는태그의 CSS선택자")

# 찾아진 태그들의 컨텐트들의 추출하여 리스트로 리턴
sapply(doms,function(x){x$getElementText()})

# 찾아진 태그들에 각각 클릭 이벤트 발생
sapply(doms, function(x){x$clickElement()})

# 가끔 clickElement() 가 일을 안 할 때가 있음…ㅜ 이 때 사용하면 좋음
remDr$executeScript("arguments[0].click();",nextPageLink)

# 페이지를 아래로 내리는(스크롤) 효과
webElem <- remDr$findElement("css", "body")
remDr$executeScript("scrollTo(0, document.body.scrollHeight)", args =
list(webElem))
```
