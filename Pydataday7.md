## 4/2 수업

#### 단계구분도

> 각기 다른 음영이나 색상 또는 값으로 각 지역과 관련된 데이터를 표현한 지도

* 지도 데이터 파일 (.geojson) - 지역에 대한 경계 정보를 제공

* 시각화 하고자 하는 데이터 파일 (.csv 등) - 지역별로 표현하고자 하는 데이터를 제공
* Choropleth와 같은 레이어를 만들 때 위의 이 두 데이터를 파라미터로 넘겨줘야 하는데 데이터는 각자 다른 파일에 있으므로, 시각화할 데이터를 지도에 얹으려면 두 데이터를 매핑해야 한다.

```
folium.Choropleth(
	geo_data = "지도 데이터 파일 경로 (.geojson, geopandas.DataFrame)"
	data = "시각화 하고자 하는 데이터파일. (pandas.DataFrame)"
	columns = (지도 데이터와 매핑할 데이터, 시각화 하고려는 데이터), 리스트나 튜플형식
	key_on = "지도 데이터 파일에서 데이터 파일과 매핑할 값 feature.properties.xxx",
	fill_color = "시각화에 쓰일 색상",[fill_opacity=, line_opacity= ,]
	legend_name = "칼라 범주 이름",
	).add_to(m)
```



### 데이터 사전처리

#### 누락 데이터 처리

* `dropna(axis = 0 or 1)`

* `isnull`: 누락데이터 = True
* `notnull`: 유효 데이터 존재 = True
* 매개변수 `thresh = 숫자`: 숫자 이상인? 



* `method = ffill`: 앞의 값으로 채우기
* `method = bfill`: 뒤의 값으로 채우기





#### 중복 데이터 처리

* `.duplicated()`



#### 데이터 표준화

* 단위 환산: 
* `.replace()`
* `.astype()`



#### 범주형 데이터 처리

* `bin`
  * `cut` 옵션?
* `label`

* 더미 변수: `get_dummies()`



#### 정규화

> 상대적인 크기가 클 때

* 0 ~ 1 이나 -1 ~ 1 사이로 변경



#### 시계열 데이터

* `timestamp`: 일정 시각
* `period` : 일정 기간

* `do_datetime()`: 다른 자료형을 Timestamp로 나타내는 datetime64 자료형으로 변환가능