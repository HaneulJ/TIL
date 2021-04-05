## 3/30 수업

### Pandas

* 가장 배우기 쉬운 프로그래밍 언어, 파이썬 기반
* 오픈소스로 무료로 이용 가능



#### 판다스 자료구조

* 목적: 형식적으로 서로 다른 여러가지 유형의 데이터를 공통의 포맷으로 정리
* 종류: 시리즈(1차원), 데이터프레임(2차원) 으로 구조화된 데이터 형식 제공



#### 시리즈 

* `Series()`
* 딕셔너리를 함수의 매개변수로 전달: `pandas.Series(딕셔너리 or 리스트)`
* 딕셔너리의 키 = 시리즈의 인덱스, 딕셔너리의 각 키 = 시리즈의 데이터 값
* 리스트 = 시리즈의 데이터 값, 시리즈의 인덱스 = 무조건 숫자 인덱스
* 서로 다른 타입 가능, 개수 제한X



##### 인덱스 구조

> 원소의 순서와 주소 저장

* 정수형 위치 인덱스: `Series[2]`, `Series[3:5(끝값 + 1)]`, `Series[[3,4]]`
* 인덱스 이름 / 인덱스 라벨: `Series['c']`, `Series[['d':'e']]`

* `.index`: 인덱스 추출  > `RangeIndex(start= 시작값, stop= 끝값+1, step= )`
* `.values`: 원소값 추출

* 튜플을 시리즈로 변환: 정수형 위치 인덱스 자동 지정, 인덱스 이름 따로 지정 가능
* 인덱스 범위 지정 선택: 정수형 인덱스 일 때는 end값 포함x



#### 데이터 프레임

> 2차원 벡터, 행렬

* `DataFrame()`

* 여러 개의 시리즈를 각 열로 모아 놓은 집합
* 딕셔너리의 키는 각 시리즈의 이름으로 ,데이터프레임의 열 이름으로
* 행 인덱스와 열 이름 지정 가능

* `rename()`: 행 인덱스나 열 이름 변경가능, `inplace=True`해야 원본 객체에서 변경
  * 기본은 False라 새로운 데이터 프레임 객체를 반환
* 행 삭제: `DataFrame 객체.drop(행 인덱스 또는 배열, axis=0)`
* 열 삭제: `DataFrame 객체.drop(열 인덱스 또는 배열, axis=1)` , 기본값



#### 인덱스

* `loc`: 인덱스 이름을 기준으로 행 선택

* `iloc`: 정수형 위치 인덱스로 행 선택, end값 제외

  * 범위 슬라이싱: `.iloc[시작 인덱스:끝 인덱스:슬라이싱 간격]`
  * 모든 행에 대하여 0행부터 2행간격으로 선택: `df.iloc[::2]`
  * 0행부터 2행까지 2행간격으로 선택: `df.iloc[0:3:2]`
  * 역순: `df.iloc[::-1]`

  

* 열 추가: `DataFrame['추가하려는 열 이름'] = 데이터 값`

* 행 추가: `DataFrame.loc['새로운 행 이름'] = 데이터 값 (또는 배열)`



* `df.set_index('새로운 인덱스', inplace=True)`: 특정 열을 행 인덱스로 설정
* `reindex(새로운 인덱스 배열)`: 행 인덱스를 새로운 배열로 재지정 가능, 기존객체 변경X
  * 기존 데이터프레임에 존재하지 않은 행 인덱스가 새롭게 추가되는 경우: NaN
* `reset_index`: 정수형 위치 인덱스로 초기화, 기존 행인데스는 열로 이동, 새로운 데이터프레임 객체로 반환
* `sort_index`: 행 인덱스를 기준으로 정렬, ascending옵션을 사용하여 오름차순/내림차순 결정, 새로운 데이터프레임 객체로 반환



#### 산술연산

> 3단계 프로세스

* 행/열 인덱스를 기준으로 모든 원소 정렬
* 동일한 위치에 있는 원소끼리 일대일 대응
* 일대일 대응이 되는 원소끼리 연산 처리, 이때 대응되는 원소가 없으면 NaN



##### 시리즈와 시리즈

* 같은 인덱스를 가진 원소끼리 계산
* 해당 인덱스에 연산 결과 매칭하여 새 시리즈를 반환
* 두 시리즈의 원소 개수가 다르거나, 시리즈의 크기가 같더라도 인덱스 값이 다를 경우: NaN



##### 연산 메소드 활용

* 객체 사이에 공통 인덱스가 없는 경우 NaN로 반환 >> `fill_value` 옵션 설정





##### 데이터 프레임과 숫자

* 기존 데이터프레임의 형태를 그대로 유지한 채, 원소 값만 새로운 값으로 바뀜
* 데이터프레임에 어떤 숫자를 더하면, 모든 원소에 숫자가 더해짐
* 타이타닉 데이터셋: Seaborn 라이브러리에서 제공하는 데이터셋



##### 데이터프레임과 데이터프레임

* 각 데이터프레임의 같은 행, 같은 열 위치에 있는 원소끼리 계산