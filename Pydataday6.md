## 3/31 수업

### 데이터 입출력

#### 외부파일 읽기

##### 판다스 데이터 입출력 도구

* CSV: `read_csv`, `to_csv`
* JSON: `read_json`, `to_json`
* HTML: ` read_html`, `to_html`
* MS  Excel: `read_excel`, `to_excel`



* CSV파일: 쉼표(,)로 열 구분, 줄바꿈으로 행 구분
  * 첫번 째 행이 행이름으로
  * 기본적으로 range 인덱스 적용 
  * `header = None`: 행 이름 지정X
  * `header = 1`: 1행을 행이름으로, 그 아래부터 데이터로 인식
  * `index_col = "c0"`: 특정 열을 인덱스로 지정 가능

* JSON 파일: key : value 구조
* HTML: `<table>`만 읽음





#### API 활용하여 데이터 수집

> 인터넷 업체가 제공하는 API를 통해 수집한 데이터를 판다스 자료 구조로 변환

* Google geo API: 장소 이름 또는 주소 입력 시, 위도와 경도 좌표 정보 변환



### 데이터 살펴보기

#### 데이터 프레임 구조

##### 데이터 요약 정보 확인

* `.shape` : 요약 
  * `.shape[0]`: 열의 개수
  * `shape[1]`: 행의 개수
* `.info()`: 기본 정보 (=str)
* `.describe()`: 기술통계 정보 요약

* `.count()`: 열의 원소 개수
* **`.value_counts()`**: 특정 열이 가지고 있는 개수 (특히 이산형, 범주형)
* `dropna = True`: NaN값을 제외하고 개수 세기, 안해주면 무조건 NaN로 나옴



* `.mean()`: 평균
* `.median()`: 중간값
* `.max()`
* `.min()`
* `.std()`: 표준편차
* `.corr()`: 상관계수





#### 판다스 내장 그래프 도구 활용

* `line`: 선 그래프
* `bar`: 수치 막대 그래프
* `barh`: 수평 막대 그래프
* `his`: 히스토그램
* `box`: 박스 프롯
* `kde`: 커널 밀도 그래프
* `area`: 면적그래프
* `pie`: 파이그래프
* `scatter`: 산점도 그래프
* `hexbin`: 고밀도 산점도 그래프
* `.map()`: 매핑하라(타입 변환)