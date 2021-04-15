## 4/15 수업

`pip uninstall pyzmq`

`pip install pyzmq`



### Spark

#### Spark의 데이터 처리 단위: RDD

> RDD: Resilent Distributed Dataset 내결합성 분산 데이터 셋

* Read Only (immutable)
* 1~n개의 partition으로 구성 가능
* 병렬적 (분산) 처리가 가능하다
* RDD 의 연산은 Transformation 연산과 Action 연산으로 나뉜다
* Transformation은 Lazy execution 을 지원
* lineage를 통해서 fault tolerant 결함 내성  확보



#### Transformation 과 Action

* RDD를 제어하는 연산
  * Transformation : RDD에서 데이터를 조작하여 새로운 RDD를 생성하는 함수
  * Action : RDD에서 RDD가 아닌 타입의 data로 변환하는 하는 함수 
  * Lineage: operation의 순서를 기록해 DAG로 표현, Transformation 연산 정보를 보관



* 연산의 수행 결과가 RDD 이면 Transformation
* Transformation 은 기존 RDD 를 이용해 새로운 RDD를 생성하는 연산 
  * 변환, 필터링 등의 작업들 : 맵 , 그룹화 , 필터 , 정렬
* Lineage 를 만들어 가는 과정이다
* 연산의 수행 결과가 정수 , 리스트 , 맵 등 RDD 가 아닌 다른 타입 이면 Action
* `first()`, `count()`, `collect()`, `reduce()`...
* Lineage 를 실행하고 결과를 만든다



* Lazy execution :Action 연산이 실행되기 전에는 Tranformation 연산이 처리되지 않는 것

* Transformation 연산은 관련 메서드를 호출하여 연산을 요청해도 실제 수행은 되지 않고 연산 정보만 보관한다 . 

* 보관만 하다가 첫 번째 Action 연산이 수행될 때 모든 Lineage 에 보관된 Transformation 연산을 한 번에 처리 한다 .
* Lazy execution 과 Lineage 를 활용함으로써 처리 효율을 높이고 클러스터 중 일부 고장으로 작업이 실패해도 Lineage 를 통해 데이터를 복구 한다



* `parallelize()` : 스칼라컬렉션 객체를 이용해서 RDD 객체를 생성
* `count()` : RDD의 요소 개수를 리턴
* `first()` : RDD 객체의 첫 번째 요소를 리턴
* `collect()` : RDD 객체의 모든 요소를 배열로 리턴
* `map()` : 입력 RDD의 모든 요소에 f를 적용한 결과를 저장한 RDD를 반환
* `flatMap()` : 입력 RDD의 모든 요소에 f를 적용하고 모든 요소들을 하나로 묶어서 반환
* `filter()` : 입력 RDD의 모든 요소에 f를 수행하고 참을 리턴하는 결과만 저장한 RDD를 반환
* `reduce()` : 지정된 f를 수행시켜 입력 RDD의 개수를 축소시켜서 생성된 RDD를 반환





###  PySpark

> Apache Spark 기능을 사용하여 Python 애플리케이션을 실행하기 위해 Python 으로 작성된 Spark 라이브러리

* PySpark 을 사용하면 분산 클러스터 다중 노드 에서 애플리케이션을 병렬로 실행 가능
* 

#### PySpark 의 장점

*  분산 방식으로 데이터를 효율적으로 처리 할 수 있는 범용인 메모리 분산 처리 엔진
* PySpark 에서 실행되는 애플리케이션은 기존 시스템보다 100배 빠르다
* 데이터 수집 파이프 라인에 PySpark 를 사용하면 큰 이점을 얻을 수 있다
* Hadoop HDFS, AWS S3 및 여러 파일 시스템의 데이터를 처리 할 수 있다
* Streaming 및 Kafka 를 사용하여 실시간 데이터를 처리하는데도 사용
* PySpark 스트리밍을 사용하면 파 일 시스템에서 파일을 스트리밍하고 소켓에서 스트리밍 가능
* 기본적으로 기계 학습 및 그래프 라이브러리가 있다



#### PySpark 아키텍처 

> Apache Spark**마스터를 드라이버라 하고 슬레이브를 작업자** 라고 하는 마스터 슬레이브 아키텍처에서 작동

* Spark 애플리케이션을 실행하면 Spark Driver 가 애플리케이션의 진입점인 컨텍스트를 생성하고 모든 작업 변환 및 작업 이 작업자 노드에서 실행되고 리소스는 Cluster Manager 에서 관리 







#### 리스트객체로 RDD 객체 생성하기

##### RDD(Resilient Distributed Dataset)

> read-only 데이터셋으로서 다양한 머신에 데이터셋의 멀티셋(중복을 허용)을 분산해두고 특정한 머신에 문제가 생기더라도 문제 없이 읽을 수 있도록 지원

- MapReduce 작업
- 분산하여 병렬적 처리
- 빠른 연산
- 불변(Immutable)
- Transformation 과 Action 으로 함수 종류가 나눠지며, Action 함수가 실행됐을 때 실제 연산
- Lineage 를 통해 Fault Tolerant(내고장성) 보장





#### 생성한 RDD 객체 Spark DataFrame 으로 변환하기

##### Spark DataFrame

- DataFrame은 명명 된 열로 구성된 데이터 세트 
- 개념적으로는 관계형 데이터베이스의 테이블 또는 R / Python의 데이터 프레임과 동일하지만 내부적으로 더욱  최적화가 있음
- RDB Table처럼 Schema를 가지고 있고 RDB의 Table 연산이 가능
- 구조화 된 데이터 파일, Hive의 테이블, 외부 데이터베이스 또는 기존 RDD와 같은 다양한 소스 에서 구성 할 수 있늠 
- DataFrame API는 Scala, Java, Python 및 R 에서 사용할 수 있음
- SparkSQL을 통해 사용 가능





### MongoDB

> NoSQL 로 분류 되는 크로스 플랫폼 도큐먼트 지향 데이터베이스 시스템

* BSON: 스키마가 고정된 구조 대신 JSON 형태의 동적 스키마형 문서를 사용



*  Document: 가장 기본적인 데이터
  * MySQL(MariaDB) 같은 RDBMS 에서 의 row
* Collection: Document 의 집합
  * RDBMS 에서는 Table 에 해당된다 
* DB: Collection 의 집합은 DB 
  * RDBMS 에서도 동일

* 장점: 똑같은 조건으로 설계되었을 시 기존 RDBMS 보다 속도가 굉장히 빠르다
* 일관성 : 모든 노드가 같은 순간에 동일한 데이터를 볼 수 있다
* 가용성 : 모든 요청이 성공 또는 실패 결과를 반환할 수 있다
* 분할내성: 메시지 전달이 실패하거나 시스템 일부가 망가져도 시스템이 계속 동작할 수 있다



##### SQL

>  시스템이 커져가면서 Scale Up 의 형태로 DB 를 증설 

* 관계를 가지는 테이블들이 수평적으로 더 커진다
* 기존에 사용하던 DB 시스템보다 고성능의 DB 시스템이 필요할 수 있음
* 굉장히 덩치가 큰 DB 시스템이 된다
* 비용도 많이 증가될 뿐만 아니라 관리가 어려워질 수 있다



##### NoSQL(Not Only SQL)

> Scale Out 의 형태로 증설 

* 여러 DB시스템으로 추가 가능

* 숫자는 무한대로 늘려갈 수 있음

* 문서 저장소: 데이터 및 메타 데이터는 데이터베이스 내의 JSON 기반 문서에 계층적으로 저장
* 키 값 저장소: NoSQL 데이터베이스 중 가장 간단한 데이터는 키 값 쌍의 컬렉션으로 표시