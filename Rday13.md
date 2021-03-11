## 3/11 수업

### dplyr 패키지

> 데이터 프레임에 담겨진 데이터들의 전처리에 가장 많이 사용되는 패키지

* 데이터 조작의 문법을 제공하며 데이터프레임을 집중적으로 다루는 툴

  

#### dplyr 패키지 방식으로 코딩

```
d <- a %>% f1 %>% f2 %>% f3
```



#### linux 명령어

* OS(Operating System 운영체제): 컴퓨터 HW가 실제 컴퓨터의 역할을 할 수 있으려면 운영체제라는 시스템 프로그램이 설치되어 있어야 한다.
  * window10, mac os, android, ios, linux, unix

* AWS: 클라우드 환경 시스템
  * linux, ls, rm, cd



#### dplyr 패키지의 주요 함수

* `distinct()`
* `sample_n()`
* `sample_frac()`
* `mutate()`
* `transmute()`
* `summarise()`



#### dplyr 패키지를 이용한 데이터 전처리 `%>%` (단축키 shift+ctrl+M)

* `filter(dataframe, filter condition1, filter condition2,...)`:  &(AND) 조건으로 row 데이터 부분집합 선별, 조건에 의한 선별
* `slice(dataframe, from, to)` :위치를 지정해서 row 데이터 부분집합 선별, 위치(position)를 사용해서 부분집합 선별
* `arrange(dataframe, order criterion 1, order criterion 2, ...)`: 데이터 프레임 행 정렬
  * 여러개의 기준에 의해서 정렬을 하고 싶으면 기준 변수를 순서대로 나열
  * 기본 정렬 옵션: 오름차순(ascending)
  * `desc()`: 내림차순 지정
* `select(dataframe, VAR1, VAR2, ...)` : 선별하고자 하는 변수 이름을 기입 

```
# "xx_name"으로 시작하는 모든 변수 선별
select(dataframe, starts_with("xx_name"))

# "xx_name"으로 끝나는 모든 변수 선별
select(dataframe, ends_with("xx_name")) 

# "xx_name"을 포함하는 모든 변수 선별
select(dataframe, contains("xx_name")) 

# 정규 표현과 일치하는 문자열이 포함된 모든 변수 선별
select(dataframe, matches(".xx_string.")) 
head(select(Cars93, matches(".P.")))
head(select(Cars93, matches("P")))

# 변수 이름 그룹에 포함된 모든 변수 선별
select(dataframe, one_of(vars)) 
vars <- c("Manufacturer", "MAX.Price", "MPG.highway")
head(select(Cars93, one_of(vars)))

# 접두사와 숫자 범위를 조합해서 변수 선별
select(dataframe, num_range("V", a:n)) 
```

* `rename(dataframe, new_var1 = old_var1, new_var2 = old_var2, ...) `: 데이터 프레임 변수 이름 변경

* `distinct(dataframe, 기준 var1, 기준 var2, ..)`: 중복없는 유일한 값 추출 

* `sample_n(dataframe, a fixed number))`:  특정 개수만큼 무작위 추출

* `sample_frac(dataframe, a fixed fraction)`:  특정 비율만큼 무작위 추출

* `sample_n(dataframe, n, replace = TRUE)` : 복원 추출

  

* `mutate()`: 파생 변수 만들기
* 그룹별 요약 처리
  * `group_by(대그룹, 중그룹, 소그룹, ...)`
  * `summarise()`

* `bind_rows()`: 두 개 이상의 데이터 프레임을 행 기준(위 - 아래 - 아래 ...)로 합칠 때 사용
* `bind_cols()`: 두 개 이상의 데이터 프레임을 열 기준(왼쪽 - 오른쪽 - 오른쪽 ...)로 합칠 때 사용