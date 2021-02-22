## 2/22 수업 [R 구문]



### 빅데이터 처리

- 데이터 수집과 저장
- EDA를 통한 시각화와 전처리
- 데이터 분석
- 분석 결과, 시각화 표현



### R

> 통계 계산과  그래픽을 위한 프로그래밍 언어이자 소프트웨어 환경이자 프리웨어!

* 데이터 - (선택) - 목표데이터 - (**전처리**) - 전처리된 데이터 - (변환) - 변환된 데이터 - (데이터마이닝) - 패턴 - (해석)



### R 구문학습내용

* r로 다룰 수 있는 데이터의 종류: 자료형(data type)
* r로 다룰 수 있는 데이터셋의 종류:  벡터, 행렬(매트릭스), 



#### 데이터(type)

* 자료형 데이터 타입
  *  문자형(character) : 문자, 문자열
  *  수치형(numeric) : 정수(integer), 실수(double)
  *  복소수형(complex) : 실수+허수
  *  논리형(logical) : 참값과 거짓값

 

* 리터럴(데이터 값)
  * 문자형(character)리터럴 :"가나다", '가나다', "", '', '123', "abc"
  * 수치형(numeric)리터럴 : 100, 3.14, 0
  * 논리형(logical)리터럴 : TRUE(T), FALSE(F)
  * `NULL`(데이터 셋이 비어있음을 의미)
  * `NA`(데이터 셋의 내부에 존재하지 않는 값(**결측치**)를 의미)
  * `NaN`(not a number: 숫자가 아님)
  * `Inf`(무한대값)

​       

* 타입채크 함수들
  * `is.character(x)`: 문자형
  * `is.logical(x)`: 논리형
  * `is.numeric(x) `: 수치형
  * `is.double(x)`: 실수형
  * `is.integer(x)`: 정수형
  * `is.null(x)`    `is.na(x)`    `is.nan(x)`    `is.finite(x)`    `is.infinite(x)`      

​         

* 자동형변환 룰: 문자형(character) > 복소수형(complex) > 수치형(numeric) > 논리형(logical)



* 강제형변환 함수: 원하는 타입으로 강제 형 변환 가능
  * `as.character(x)`
  * `as.complex(x)`
  * `as.numeric(x)`
  * `as.double(x)`
  * `as.integer(x)`
  * `as.logical(x)`       



* 자료형 또는 구조 확인 함수:`class(x)`, `str(x)` 행열 개수 체크, `mode(x)`, `typeof(x)`



#### 데이터 셋

> 벡터(1차원), 행열(2차원), 배열(n차), 데이터프레임(csv), 리스트

* 동일한 유형의 데이터만 지정: 벡터, 행열, 배열
* 서로 다른 유형의 데이터: 데이터프레임
* 저장할 수 있는 데이터의 타입/종류 제한 X: 리스트
* factor(요인): 정해진 범주의 값만 저장 categorical data



##### 벡터

>  가장 기초적인 데이터 셋(데이터 구조), 1차원으로 사용, 기본 열 벡터(행으로 출력)

* 동일 타입의 데이터만으로 구성 (문자형 > 수치형 > 논리형)
* 스칼라 X, 하나의 원소로 구성되는 벡터로 간주
* 생성 방법
  * `c()`: 아규먼트를 원하는 만큼 전달 가능
  * `seq()`: range 함수와 비슷
  * `rep()` 데이터 값을 반복해서~
  * `:` : 1씩 증가/감소하는 데이터

* 미리 정의된 내장 상수 벡터들: `LETTERS`, `letters`, `month.name`, `month.abb`, `pi`
* 인덱싱: **1**부터 시작하는 인덱스값과 `[인덱스]` 연산자 사용
* 주요 함수
  * `length()`: `len()`과 같음
  * `names()`: 벡터를 구성하는 요소마다 이름 설정, 추출 가능
  * `sort()`: 오름차순 정렬, 아규먼트 지정 시 내림차순 가능
  * `order()`: 벡터가 가지고 있는 원소 값들을 비교해서 *인덱스*로 리턴(데이터 프레임으로 정렬할 때 유용)

```
# 음의 값 인덱스: 제외!!, -1: 첫 번째 인덱스의 값만 빼고 추출, 
LETTERS[-1]; LETTERS[c(-2,-4)] 
```



```
class(x) # 벡터 값의 타입
rev(x)  # 벡터 값을 역순으로 추출
range(x) # 제일 작은 값 & 제일 큰 값 추출 
sort(x)
sort(x, decreasing = TRUE) # decreasing: 기본값이 false라 TRUE시 내림차순
order(x) # 데이터 값 오름차순, 그 값에 해당하는 인덱스 추출

x + 1 # 각각의 원소값에 1를 더한다

seq(1, 10, by=3) # 1~10 사이 숫자 중 3씩 증가한 숫자만 추출
```



```
x[c(2,4)] # x[2], x[4] 인덱스에 해당되는 값을 추출
[1]  5 11

x[c(F,T,F,T,F)] # 논리형 인덱스도 가능, T만 추출 
[1]  5 11

# x[c(T,F)]: x[c(T, F, T, F, T)] 원소 개수만큼 반복(확장)
[1]  5 11

x > 5 # 비교해서 논리형으로 추출
[1] FALSE FALSE  TRUE  TRUE  TRUE

x[x > 5] # 인덱스에 비교식을 넣으면 해당하는 값이 추출
[1] 21 11 16
```

* `&` (and): 원소 마다 적용 가능
* `&&`: 하나의 값(맨 앞 데이터)만 가지고 연산, 벡터 연산X

* `|`(or)
* `||`

```
> c(T, T, F, F) & c(T, F, T, F)
[1]  TRUE FALSE FALSE FALSE

> c(T, T, F, F) | c(T, F, T, F)
[1]  TRUE  TRUE  TRUE FALSE

> c(T, T, F, F) && c(T, F, T, F)
[1] TRUE

> c(T, T, F, F) || c(T, F, T, F)
[1] TRUE
```



```
names(x) # 인덱스 대신 names 부여, 텍스트마이닝 할 때 많이 이용
names(x) <- LETTERS[1:5]
names(x) <- NULL # names 지우기

> names(x)
NULL
> names(x) <- LETTERS[1:5]
> x
 A  B  C  D  E 
 3  5 21 11 16

```

```
ls() # 어떤 함수 있는지 나열
rm(x) # 함수 삭제
```

```
rainfall <- c(21.6, 23.6, 45.8, 77.0, 
              102.2, 133.3,327.9, 348.0, 
              137.6, 49.3, 53.0, 24.9)
rainfall > 100 #100보다 크면 true
rainfall[rainfall > 100] #비교식을 인덱스로 하여 해당하는 데이터만 출력, 몇 월 데이터인지 모름
which(rainfall > 100) #which 함수에 아규먼트로, 해당 데이터의 인덱스값만 꺼내고 싶을때 사용
month.name[which(rainfall > 100)]
month.abb[which(rainfall > 100)] #축약된 형태의 월 이름으로 추출
month.korname <- c("1월","2월","3월",
                   "4월","5월","6월",
                   "7월","8월","9월",
                   "10월","11월","12월")
month.korname[which(rainfall > 100)]
which.max(rainfall) # 아규먼트로 주어진 벡터에서 최대값의 인덱스 추출
which.min(rainfall) # 최소값의 인덱스 추출
month.korname[which.max(rainfall)] 
month.korname[which.min(rainfall)]
```

* `sample(추출할 벡터, 추출할 개수)` :중복X (replace=F) 기본값
* `paste("I'm","Duli","!!")`: 여러 문자열을 하나의 문자열로 결합 (blank 기본)
  * 중간 blank 제외하고 싶을 때: `paste0`
  * `collapse`: 결합된 문자열들을 또 하나의 문자열로 결합
    
    

```
> paste("I'm","Duli","!!")
[1] "I'm Duli !!"

> paste("I'm","Duli","!!", sep="")
[1] "I'mDuli!!"

> paste0("I'm","Duli","!!")
[1] "I'mDuli!!"

> fruit <- c("Apple", "Banana", "Strawberry")
> food <- c("Pie","Juice", "Cake")
> paste(fruit, food)
[1] "Apple Pie"       "Banana Juice"    "Strawberry Cake"

> paste(fruit, food, sep="")
[1] "ApplePie"       "BananaJuice"    "StrawberryCake"


> paste(fruit, food, sep="", collapse="-")
[1] "ApplePie-BananaJuice-StrawberryCake"
```





##### 행렬

> 2차원 벡터

* 동일 타입의 데이터만으로 구성

* 인덱싱: [행 인덱싱, 열 인덱싱], [ , ] .. 생략 시 모든 행/열
  * `drop 속성`: 행렬 구조 유지 여부(차원을 축소하지 말아라?)
  * `drop = False` 가 기본 (구조 깨뜨리기)
* 행렬 생성방법: 열 우선으로 채움
  * **`matrix(data=벡터, nrow=행의 갯수, ncol=열의 갯수)`**
  * `matric(data=벡터, nrow=행의 갯수, ncol=열의 갯수, byrow=TRUE)`: 행 우선으로 채움
  * `rbind(벡터들)`: 행 단위로 붙여~
  * `cbind(벡터들)`: 열 단위로~
* `dim(m)`: 행렬이 몇 차원인지 체크, `nrow()`, `ncol()`
* `colnames(m)` `rownames(m)`
* `rowSums(m)`, `colSums(m)`
* `rowMeans(m)`, `colMeans(m)`
* `sum(m)`, `mean(m)`

* `apply(m, 1 또는 2, 함수)`