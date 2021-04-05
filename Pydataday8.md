## 4/5 수업

문자열 뒤에 저장되어있는 : 시리즈(오브젝?)

데이터값 자체: datatype64???



#### 시계열 데이터

* `freq = "MS"`: 월의 시작일
* `freq= "M"`: 월의 마지막일

* 날짜 데이터 분리: `dt.~`

* `DatetimeIndex`, `PeriodIndex`: 타입별로 구성된 열을 행 인덱스로 지정할 때



### 데이터프레임의 다양한 응용

#### 함수 매핑

<span style="color:red">Series와 DataFrame에 함수 적용하기</span>

* map, apply 함수 : Series에서 사용하며 **모든 요소에 함수 일괄 적용**
* apply 함수 : DataFrame에서 사용하며 각각의 행 또는 열(Series)에 함수 일괄 적용
  * `.apply()`
* applymap 함수 : DataFrame에서 사용하며 모든 요소에 함수 일괄 적용

#### 

* `df.pipe(함수1).pipe(함수2)`



#### 열 재구성

* `DataFrame 객체[재구성한 열 이름의 리스트]`
* `df.columns`: 
* `df.columns.values`: 실제 컬럼명만 리스트로 추출



#### 필터링

* 불린 인덱싱: 조건식이나 비교식 가능
* `isin()` 메소드 활용: 데이터프레임의 열에서 추출하려는 값들로 이루어진 리스트 만듬
* 



#### 데이터프레임 합치기

* `pd.concat()`: 데이터프레임 연결, 시리즈를 행/열 별로 연결도 가능
  * 인덱스가 중복일 경우: 새로 부여 `ignore_index = True`
  * `join = outer`: 값이 없으면 만들어서 붙여라? (기본값, NaN로 채워짐)
  * `join = inner`: 행 인덱스의 교집합끼리 붙인다?



* `pd.merge()`: 데이터프레임 병합
  * SQL의 join구문과 유사
  * `how = "inner"`: 기본값





* `df.join`: 데이터프레임 결합

