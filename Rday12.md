## 3/10 수업

### 데이터 시각화

> 데이터 셋 파악

* 시각화 함수의 종류
  * 고수준 함수: plot(), boxplot(), hist(), pie(), barplot()
  * 저수준 함수: title(), lines(), axis(), legend(), points(), text()
  * 칼라팔레트 함수: rainbow(), cm.colors(), topo.colors(), terrian.colors(), heat.colors()





#### 막대 그래프

* 테이블 객체(네임드 벡터 형식으로 저장되어 있는)

```
ds <- table(favorite)
ds  # 
barplot(ds, main= "그래프 제목", col="색깔(막대마다 색 지정 가능)/팔레트 기능 가능", horiz=T(수평방향 출력), names=c('막대 이름 변경 가능'), las=2(막대 이름을 세로로 배치), density=coldens)

#
coldens <- seq(from=10, to=10, by=10)
density=coldens : 막대 안에 색깔 채우기

# 중첩그룹 막대 옆으로 나열 
beside=T 

# 범례 
legend.text = T
legend.text= c(" ", " "..) 범례 이름 변경 가능

# 그래프 밖에 범례 표시
args.legend = list(x= 'topright(위치)', bty='n', inset=c(-0.25,0))
# bty: 범례가 표시되는 영역에 테두리선을 표시할지 여부 지정
o: 테두리선 표시
n: 테두리선 표시 x
# insec: -0.25 (x축 반대방향), 0 (y축) 이동

par(mfrow=c(1,1), mar=c(아래, 왼쪽, 위, 오른쪽))
# mfrow=c(1,1): 창을 분할하지 않음
# mar=c(아래, 왼쪽, 위, 오른쪽): 여유공간 지정
```

* las 값
  * 0: 축 방향(기본)
  * 1: 수평방향 (축 방향과 상관X)
  * 2: 축 기준으로 수직방향
  * 3: 수직방향 (축 방향과 상관X)





#### 히스토그램

> 그룹이 명시적으로 존재하지 않는 수치형(연속형) 자료의 분포를 시각화할 때 사용

* 관측값들이 어느 구간에 어느 빈도로 분포하는지 쉽게 파악 가능

```
hist(수치형 데이터가 담겨져 있는 벡터,
	  main = "그래프 제목",
	  xlab = "x축 이름",
	  ylab = "y축 이름",
	  border = "막대 테두리 색",
	  col = "막대 색",
	  las = x축 글씨방향,
	  breaks = 몇 개의 구간으로 나눠서 출력할지(지정하지 않아도 알아서 판단해서 최적으로 출력)
	  )
	  
# 구간별 빈도수 저장	  
freq <- result$counts

# 구간별 빈도수 이름 가능
names(freq) <- 

```







#### 다중그래프

```
# 화면 분할 2행 2열로!
par(mfrow=c(2,2), mar=c(3,3,4,2))

그래프1
그래프2
그래프3
그래프4



# 화면분할 취소
par(mfrow=c(1,1), mar=c(5,4,4,2)+.1)
```



#### 그래프 저장

* 플롯창에 표시
* 플롯창 하단의 [Zoom]클릭 시 Plot Zoom 팝업창 표시
* API로도 저장 가능





#### 원그래프

```
pie(ds, main="제목", col=c("색1", "색2", ..), radius=1)
# ds에 저장된 값들을 원 안에서 시계 반대 방향으로 따라가며 파이조각으로 표시
# 시작위치: 3시방향, 반시계

# 라벨 두 줄로 나타내기
pie(성적$국어, labels=paste(성적$성명,"\n","(",성적$국어,")"), col=rainbow(10))
```





#### 선그래프

> 시간의 변화에 따라 수집된 데이터(시계열 데이터) 시각화, 연도별 인구증가 추이

* x축: 시간축

```
plot(x data,
	 y data,
	 main = "제목",
	 type = '그래프 종류 선택',
	 lty = 선의 종류 선택,
	 lwd = 선의 굵기 선택,
	 xlab = "x축 레이블",
	 ylab = "y축 레이블"
	 )
```





#### 복수의 선그래프

```
plot(x data,
	 y data,
	 main = "제목",
	 type = '그래프 종류 선택',
	 lty = 선의 종류 선택,
	 lwd = 선의 굵기 선택,
	 xlab = "x축 레이블",
	 ylab = "y축 레이블"
	 )
lines(x data,
	  y2 data,
	  type = '',
	  col = "")
# y2 data lines만 추가!
```



#### 원그래프와 선그래프로 데이터 정리하기

```
LAB
```



#### 상자그래프

> 사분위수를 시각화하여 그래프 형태로 나타냄

* 하나의 그래프로 데이터의 분포 등 다양한 정보 전달하여 단일변수 수치형 자료를 파악하는데 자주 사용
* 이상치 여부 판단

```
> boxplot.stats(dist)
최솟값, 1사분위수, 중앙값, 3사분위수, 최댓값

> $n
관측값 개수

> $conf

```



* 그룹이 있는 데이터의 상자그림

```
# 꽃입의 길이(Petal.Length)를 품종별로 나누어서 그리기
boxplot(Petal.Length~Species, # 데이터와 그룹 정보(Species: 그룹 정보가 있는 열)
		data = 				  # 데이터가 저장된 자료 구조
		main = )
		
# data 생략 가능
boxplot(iris$Petal.Length ~ iris$Species,
		main = )
```



* `,`로 구분되어 있는 데이터로 박스 그래프 그리기

```
data <- read.table("온도.txt", header=TRUE, sep=",")

# 
chtcols = rep(c("red","sienna","palevioletred1","royalblue2"), times=3)
```





#### 산점도

> 다중변수 데이터에서 두 변수에 포함된 값들을 2차원 그래프 상에 점으로 표현하여 분포 관찰



```
plot( x축 데이터,
	  y축 데이터,
	  # mtcars$wt, mtcars$mpg
	  # mtcars[,c('wt','mpg')]  열 지정?
	  # mpg~wt, data = mtcars
	  
	  
	  main = "제목"
	  type="p"
	  pch = 점의 모양 지정(0~25, 문자)
```



#### 여러 변수들 간의 산점도

> 변수가 2개 이상인 데이터에 대해 변수를 2개씩 짝지어 산점도 작성

* 대각선을 기준으로 대칭 이룸
* 두 변수가 만나는 지점이 두 변수에 대한 산점도



#### 그룹정보가 있는 2개 변수의 산점도

> 그룹 정보를 알고 있을 경우 각 그룹별 관측값을 다른 색과 모양으로 표시 가능

​	

```
iris.2 <- iris[,3:4]  # 데이터 준비
levels(iris$Species)  # 그룹 확인
group <- as.numeric(iris$Species)  # 점의 모양과 색, 팩터 타입을 숫자로 변경
group
color <- c('red', 'green', 'blue')
plot(iris.2,
     main = " "
     pch = c(group),
     col = color[group])
```



#### 산포도

```
par(mar=c(5,5,5,5), mfrow=c(1,1))
plot(국어, type="o", col="blue", ylim=c(0,12), axes=F, ann=F)
# axes=F, ann=F: x축, y축, 라벨 삭제

axis(1, at=1:10, lab=c("01","02","03","04", "05","06","07","08","09","10")) # x축 추가
axis(2, at=c(0,2,4,6,8,10)) # y축 추가
```



* 그래프를 이미지 파일로 저장할 때

```
# 그려지는 그래프를 파일에 저장하는 방법
ymax <- max(성적$국어) #성적 데이터 중에서 최대값을 찾는다(y 축의 크기 제한)
pcols<- c("red","blue","green")
png(filename="성적.png", height=400, width=700, bg="white") # 출력을 png파일로 설정

plot(성적$국어, type="o", col=pcols[1], ylim=c(0, ymax), axes=FALSE, ann=FALSE)
axis(1, at=1:10, lab=c("01","02","03","04","05","06","07","08","09","10"))
axis(2, at=0:5, lab=c(0,2,4,6,8,10))
box()
lines(성적$수학, type="o", pch=16, lty=2, col=pcols[2])
lines(성적$영어, type="o", pch=23, lty=3, col=pcols[3] )
title(main="성적그래프", col.main="red", font.main=4)
title(xlab="학번", col.lab=rgb(1,0,0))
title(ylab="점수", col.lab=rgb(0,0,1))
legend(1, ymax, names(성적)[-1], cex=0.8, col=pcols, pch=c(21,16,23), lty=c(1,2,3))

dev.off() #출력 종료
```

```
# 그래프를 그린 후에 파일에도 저장하는 방법
dev.copy(png(타입형식), “mytest.png”) 또는 dev.copy(pdf, “mytest.pdf”)
dev.off()
```



