## 3/9 수업



### 텍스트 마이닝(tm 패키지)

> 텍스트 데이터의 정제작업을 다원하는 다양한 변환함수 제공

* `getTransformations()`: 사용 가능한 변환함수의 리스트 확인
* `tm_map()`: 인수로 전달하여 변환작업 처리 가능
* stemming: 문서에서 문장부호 제거, 모두 소문자로 변환, 단어의 어간 추출 등
* `# 코퍼스`: 단어 주머니?



```
corp2. <- tm_map(corp1,stripWhitespace) # 여러 개의 공백을 하나의 공백으로 변환한다.
corp2. <- tm_map(corp2.,removeNumbers) # 숫자를 제거한다.
corp2. <- tm_map(myCorpus, content_transformer(tolower)) # 영문 대문자를 소문자로 변환한다.
corp2. <- tm_map(corp2.,removePunctuation) # 마침표,콤마,세미콜론,콜론 등 문자 제거한다.
corp2. <- tm_map(corp2.,PlainTextDocument)
stopword2. <- c(stopwords('en'),"and","but") # 기본 불용어 외에 불용어로 쓸 단어 추가
# en: 나라이름과 같은 코드명(ko는 안됌)

corp2. <- tm_map(corp2.,removeWords,stopword2.) # 불용어 제거하기 (전치사 , 관사 등)
```





#### 코퍼스

> 언어학에서 구조를 이루고 있는 텍스트 집합

* 통계 분석 및 가설 검증, 언어 규칙의 검사 등에 사용

* `getSources()`: 사용 가능한 소스 객체의 종류 파악 가능

* 비정형의 텍스트를 구조화된 데이터로 변환

* 예제

```
lunch <- c("커피 파스타 치킨 샐러드 아이스크림",
"커피 우동 소고기김밥 귤",
"참치김밥 커피 오뎅",
"샐러드 피자 파스타 콜라",
"티라무슈 햄버거 콜라",
"파스타 샐러드 커피"
)

cps <- VCorpus(VectorSource(lunch))
tdm <- TermDocumentMatrix(cps)
tdm
(m <- as.matrix(tdm))
# 1,2 글자는 사라짐

cps <- VCorpus(VectorSource(lunch))
tdm <- TermDocumentMatrix(cps,
control=list(wordLengths = c(1, Inf)))  # 글자 길이 1~무한대: 제한 없음
tdm
(m <- as.matrix(tdm))

rowSums(m)
colSums(m)
com <- m %*% t(m) 
# 동시출현(Co-occurrence)이란 한 문장, 문단 또는 텍스트 단위에서 같이 출현한 단어를 가리킨다.
```

* 예제

```
library(tm)
A <- c('포도 바나나 딸기 맥주 비빔밥 여행 낚시 떡볶이 분홍색 듀크 귤')
B <- c('사과 와인 스테이크 배 포도 여행 등산 짜장면 냉면 삼겹살 파란색 듀크 귤 귤')
C <- c('백숙 바나나 맥주 여행 피자 콜라 햄버거 비빔밥 파란색 듀크 귤')
D <- c('귤 와인 스테이크 배 포도 햄버거 등산 갈비 냉면 삼겹살 녹색 듀크')
data <- c(A,B,C,D)
cps <- Corpus(VectorSource(data))
tdm <- TermDocumentMatrix(cps)
inspect(tdm)
m <- as.matrix(tdm)
v <- sort(rowSums(m), decreasing=T)
inspect(tdm) 
m <- as.matrix(tdm) 
v <- sort(rowSums(m), decreasing=T)
m1 <- as.matrix(weightTf(tdm))     #
m2. <- as.matrix(weightTfIdf(tdm)) # 
m1;m2.
```

* 단어 가중치: 문서에서 어떤 단어의 중요도를 평가하기 위해 사용되는 통계적인 수치
  * TF : Term Frequency(단어빈도) 기본 디폴트
  * IDF : Inverse Document Frequency(역문서빈도)
  * DF : Document Frequency(문서빈도) 몇 개의 문서에서 등장했는지
  * TFIDF : TF X IDF
  * 특정 문서 내에서 단어 빈도가 높을 수록, 전체 문서들엔 그 단어를 포함한 문서가 적을 수록 TFIDF 값이 높아지게 된다. 즉, 문서 내에서 해당 단어의 중요도는 커지게 된다.
* 예제

```
html.parsed <- htmlParse("TextofSteveJobs.html") 
text <- xpathSApply(html.parsed, 
path="//p", xmlValue) # 조상이 누구든 p 포함
text 
text <- text[4:30] 
text 
docs <- VCorpus(VectorSource(text)) 
docs

# content_transformer: 리턴값 함수
toSpace <- content_transformer(function(x, pattern){return(gsub(pattern, " ", x))})
docs <- tm_map(docs, toSpace, ":")
docs <- tm_map(docs, toSpace, ";")
docs <- tm_map(docs, toSpace, "'")
docs[[17]]
docs[[19]]
docs[[17]]$content
docs[[19]]$content
docs <- tm_map(docs, removePunctuation) # 특수문자 없애기
text[17]
docs[[17]]$content
```





#### 텍스트 마이닝의 결과 시각화





#### 문서 간 유사도 분석

* DTM: 문서의 각 단어들을 수치화하여 표현
* 코사인 유사도, 유클리드 거리



* 코사인 유사도: 두 벡터 간의 코사인 각도를 이용하여 유사도 측정
  * 두 벡터의 값이 완전 동일하면 1, 반대 방향이면 -1, 90도의 각을 이루면 0이 된다.
  * 1에 가까울 수록 유사도가 높다.

* 유클리드 거리: 두 점 사이의 유클리드 거리 공식은 피타고라스의 정리를 통해 두 점 사이의 거리를 구하는 것과 동일