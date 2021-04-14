## 4/14 수업

### pymysql을 이용한 MariaDB 연동

*  `connect()` 함수를 이용하면 MySQL(MariaDB) host내 DB와 직접 연결 가능
* user: user name
* passwd: 설정한 패스워드
* host: DB가 존재하는 host
* db: 연결할 데이터베이스 이름
* charset: 인코딩 설정



#### Cursor 객체 생성

* 연결한 DB와 상호작용하기 위해 cursor 객체를 생성해주어야 한다.

* 다양한 커서의 종류가 있지만, 데이터 분석가에게 익숙한 데이터프레임 형태로 결과를 쉽게 변환할 수 있도록 **딕셔너리** 형태로 결과를 반환해주는 **DictCursor**객체를 주로 사용한다.

* 일반 **Cursor**객체를 사용하면 결과가 일반적으로는 **튜플** 형태로 리턴된다.

* SELECT 명령을 위해 SQL 문을 따로 변수에 넣어주고 `cursor.execute(sql)` 을 사용해 SQL를 실행한다.

* 실행한 결과를 `fetchall()`,`fetchone()` 등으로 받아 온다.

* `fetchall()`: 모든 데이터를 한 번에 가져올 때 사용

* `fetchone()`: 한 번 호출에 하나의 행만 가져올 때 사용

* `fetchmany(n)`: n개만큼의 데이터를 가져올 때 사용





### Hadoop

* **HDFS**: A file system to manage the storage of data (Storage)
* **MapReduce**: A framework to process data across multiple servers (Computation)





##### 분산 컴퓨팅 시스템



##### 클러스터

>  여러 대의 컴퓨터들이 연결되어 하나의 시스템처럼 동작하는 컴퓨터들의 집합





#### Hadoop HDFS 명령어

* `hdfs dfs -ls/ [디렉토리명 또는 파일명]`
  : 지정된 디렉토리의 파일리스트 또는 지정된 파일의 정보를 보여준다
* `hdfs dfs -ls R/ [디렉토리명]`
  : 지정된 디렉토리의 파일리스트 및 서브디렉토리들의 파일 리스트도 보여준다
* `hdfs dfs -mkdir/ [디렉토리명]`
  : 지정된 디렉토리를 생성한다
* `hdfs dfs -cat/ [디렉토리 파일]`
  : 지정된 파일의 내용을 화면에 출력한다
* `hdfs dfs -put 사용자계정로컬파일 HDFS 디렉터리 [/파일]`
  : 지정된 사용자계정 로컬 파일시스템의 파일을 HDFS 상 디렉터리의 파일로 복사한다
* `hdfs dfs -get HDFS 디렉터리의파일 사용자계정로컬 디렉터리 [/파일]`
  : 지정된 HDFS 상의 파일을 사용자계정 로컬 파일시스템의 디렉터리나 파일로 복사한다
* `hdfs dfs -rm / [디렉토리] /파일`
  : 지정된 파일을 삭제한다
* `hdfs dfs -rm r / 디렉토리`
  : 지정된 디렉터리를 삭제 . 비어 있지않은 디렉터리도 삭제하며 서브 디렉토리도 삭제한다
* `hdfs dfs -tail/ [디렉토리] / 파일`
  : 지정된 파일의 마지막 1kb 내용을 화면에 출력한다
* `hdfs dfs -chmod 사용자허가모드 / [디렉토리명 또는 파일명]`
  :지정된 디렉토리 또는 파일의 사용자 허가 모드를 변경한다
* `hdfs dfs -mv /[디렉토리]/ old 파일/ [디렉토리]/ new 파일`
  : 지정된 디렉토리의 파일을 다른 이름으로 변경하거나 다른 폴더로 이동한다




#### Hadoop MapReduce

> 대용량 데이터 처리를 분산 병렬 컴퓨팅에서 처리하는 소프트웨어 프레임워크

* 페타바이트 이상의 대용량 데이터를 신뢰도가 낮은 컴퓨터로 구성된 클러스터 환경에서 병렬 처리를 지원
* Hadoop 클러스터의 데이터를 처리하기 위한 시스템
* Map 과 Reduce사이에는 shuffle 과 sort 라는 단계 존재
  * Map task:  전체 데이터 셋에 대해서 별개의 부분에 대한 작업을 수행하게 되는데 , 기본적으로 하나의 HDFS block 을 대상으로 수행
  * 모든 Map 태스크가 종료되면 , MapReduce 시스템은 중간 intermediate 데이터를 Reduce 단계를 수행할 노드로 분산하여 전송
* Distributed File System에서 수행되는 MapReduce 작업이 끝나면 HDFS에 파일이 써짐
*  MapReduce 작업이 시작: HDFS로 부터 파일을 가져오는 작업 수행





#### Apache Spark

> 메모리 내 처리를 지원하여 빅데이터를 분석하는 애플리케이션의 성능을 향상시키는 오픈 소스 병렬 처리 프레임워크

