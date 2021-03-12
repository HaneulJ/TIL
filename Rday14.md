## 3/12 수업

### ggplot2 패키지를 활용한 데이터 시각화

> 그래프 기능 제공

* 동일한 문법으로 다양한 그래프 
* 비교적 쉽게 높은 수준의 그래프



#### plot의 구성요소

* layers
* scales
* coordinate system
* facetting spectification



#### ggplot2 패키지

* Data: 데이터 프레임
  * 데이터의 기록 방식: long-farmat에 기반한 tidy data
* (Aesthetic)Mapping: 데이터의 요소와 그래프의 요소를 대응시키는 과정
  * 하나의 변수가 여러 가지 시각적 요소에 대응 가능
* Geometric Object(geom): 어떤 형태의 그래프를 그릴지 지정
* Position: 그래프에서 각 도형이 어떤 식으로 배치될 지 결정
* Statistical Transformation(stat):값이 어떻게 그래프에 반영되는지 결정



#### ggplot2 패키지로 그래프 그리는 과정

1. 배경 설정
   * x축 displ, y축 hwy로 지정해 배경 생성 `ggplot(data = mpg, aes(x = displ, y = hwy))`
2. 그래프 추가
   * 배경에 산점도 추가 `ggplot(data = mpg, aes(x = displ, y = hwy)) + geom_point()`
3. 축 범위를 조정하는 설정 추가
   * x축 범위 3~6으로 지정 `ggplot(data = mpg, aes(x = displ, y = hwy)) + geom_point() + xlim(3, 6)`
4. 축 범위를 조정하는 설정 추가
   * x축 범위 3~6, y축 범위 10~30으로 지정 `ggplot(data = mpg, aes(x = displ, y = hwy)) +
     geom_point() + xlim(3, 6) + ylim(10, 30)`

5. 칼라와 점모양 추가 
   * `ggplot(data = mpg, aes(x = displ, y = hwy)) + geom_point(shape=21, size=6, colour="blue") + xlim(3, 6) + ylim(10, 30)`
6. Drv 변수별로 칼라 설정
   * `ggplot(data = mpg, aes(x = displ, y = hwy, col=drv)) + geom_point()`



* `df_mpg <- mpg %>% group_by(drv) %>% summarise(mean_hwy = mean(hwy))`

* 집계 막대 그래프

  `ggplot(data = df_mpg, aes(x = drv, y = mean_hwy)) + geom_col()`

* 빈도 막대 그래프

  `ggplot(data = mpg, aes(x = drv)) + geom_bar()`

* 선 그래프(주로 시계열 그래프)

  `ggplot(data = economics, aes(x = date, y = unemploy)) + geom_line()`

* 상자 그림

  `ggplot(data = mpg, aes(x = drv, y = hwy)) + geom_boxplot()`





#### ggplot2 그래프로 인터랙티브 그래프 만들기

```
install.packages("plotly")
library(plotly)

p <- ggplot(data = mpg, aes(x = displ, y = hwy, col = drv)) + geom_point()
ggplotly(p)

p <- ggplot(data = diamonds, aes(x = cut, fill = clarity)) +
geom_bar(position = "dodge")
ggplotly(p)
```



#### 트리맵 그리기

```
# 트리맵 라이브러리 설치
install.packages("treemap")
# 트리맵 메모리 로드
library(treemap)

sales_df <- read.xlsx("data/data.xlsx", 2, encoding="UTF-8")
# 트리맵 그리기
# index에 표현하고 싶은 계층 순서대로 벡터로 생성. product, region 순으로 벡터를 지정함으로써 
# product가 region보다 더 상위로 구분이 됨
treemap(sales_df, vSize="saleAmt", index=c("product", "region"), title="A기업 판매현황", fontfamily.title="maple", fontfamily.labels="maple")

# 트리맵 그리기
treemap(sales_df, vSize="saleAmt", index=c("region", "product"), title="A기업 판매현황", fontfamily.title="dog", fontfamily.labels="dog")
```

