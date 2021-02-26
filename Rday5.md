## 2/26 수업

#### 파일에서 데이터 읽어들이기

```
nums <- scan("sample_num.txt")
words_ansi <- scan("sample_ansi.txt", what="")
words_utf8 <- scan("sample_utf8.txt", what="", encoding="UTF-8")
lines_ansi <- readLines("sample_ansi.txt")
lines_urf8 <- readLines("sample_utf8.txt", encoding="UTF-8")
df1 <- read.csv("CSV파일 또는 CSV를 응답하는 URL")
df2 <- read.table("일정한 단위(공백 또는 탭등)로 구성되어 있는 텍스트 파일 또는 URL")
(필요에 따라서 stringsAsFactors 속성 사용)

write.csv(파일명), write.table(파일명): 저장할 때
```

* xxx.csv : `read.csv()`, data.frame으로 읽음, 첫번째 행은 컬럼명으로 인식
* zzz.log : `read.table()`, data.frame으로 읽음, 첫 번째  행부터 데이터로 인식, head=TRUE를 하면 컬럼명 인식
* xzx.txt
  *  `scan()` 벡터(워드:공백 등 단위로)로 읽음, `what=""` 매개변수에 null로 주면 문자형으로 인식(기본 수치형)
  * `readLines()` 벡터로(행 단위로) 읽음





* 각 나라마다 그 나라 고유의 코드셋이 있음
  * 코드셋: 컴퓨터에서 문자를 표현하기 ㅜ이해 문자마다 부여한 숫자값
* 0x00~0x7F : ASCII 코드값(전 세계 표준)
* 0xB0A1~ : 가~힣
  * KSC5601, EUC-KR, CP949, 메모장(ansi)
  * 영문 1바이트, 한글 2바이트
* 0xEAB080: UNICODE, UTF-8(코드값 단일화)
  * 1바이트~4바이트
  * 영문 1바이트, 한글 3바이트



* 지금까지 만들어진 모든 객체들을 파일에 보관 `save()`, 읽어오기: `load()`



* `apply(매트릭스, 1, 함수)`
* `apply(매트릭스, 2, 함수)`
  * `sapply(벡터, 함수)`: 벡터가 가지고 있는 원소값들을 한번씩 전달하면서 함수 호출, 리턴값(단순한 객체)
  * `lapply(벡터, 함수)`: 리턴값 무조건 list
  * `tapply()`
  * `mapply()`





#### 사분위수

> 자료를 크기순으로 배열하고, 누적 백분율을 4등분한 각 점에 해당하는 값

* `quantile()`
* 25% 별
* 제 2 사분위수 = 누적 백분율 50% : 중앙값
* 1/4 분위수 : 중간값의 왼쪽 데이터들
  * 홀수 갯수 : 중간값 + (중간값의 다음값 - 중간값) * 0.25
  * 짝수 갯수 : 중간값 + (큰값 - 작은값) * 0.25
* 3/4 분위수 : 중간값의 왼쪽 데이터들
  * 홀수 갯수 : 중간값 - (중간값 - 중간값 이전값) * 0.25 
  * 짝수 갯수 : 중간값 - (큰값 - 작은값) * 0.25





### R

> 스크립트 언어

* 패키지 제공