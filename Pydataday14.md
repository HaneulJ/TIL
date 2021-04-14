## 4/13 수업



### SQL 학습



* DBMS(데이터베이스 관리 시스템): Define, record, query, update, manage data

  * **CRUD: Create, Read, Update, Delete**  >> 표준 언어: **SQL**(Structured Query Language)

  * C: insert into 테이블명[(컬럼명리스트, ...)] values(데이터값리스트, ...)

  * R: select 컬럼명, ...

       [ from 테이블명

    ​     where 조건식 *(이게 없으면 모든 행 추출)*

    ​     group by 그룹핑 기준 컬럼 또는 식, ...

    ​     having 그룹조건

    ​     order by 정렬기준컬럼 [기본: asc, desc] , ... ]

    * 마리아 DB   select now(); 
    * 오라클 DB   select sysdate from dual;  

    ```
    select * from t where empno = 100
    select * from t where empno != 100
    select * from t where ename = 'King'  # 문자열데이터갑시 단일인용부호만('')
    
    select * from t where enmae = 'King' or ename = 'Kang' or ename = 'Kong'
    select * from t where ename in ('King', 'Kang', 'Kong')
    select * from t where ename like 'K%'  
    # %: 0개 이상의 임의의 문자
    # _: 임의의 한 문자
    
    # 중복되는 값 제외
    select distinct ~~
    
    # 연산자 우선순위
    1. 산술
    2. 연결
    3. 비교
    4. is (not) null, like, (not) in
    5. (not) between, and
    6. 논리연산자 not
    7. 논리연산자 and
    8. 논리연산자 or
    ```

    

  * U: update 테이블명 set 컬럼명=컬럼값, ...[where 조건식]

  * D: delete [from] 테이블명 [where 조건식]

  * undo 기능: commit, rollback

* Storage area: Relational / Hirarchical / Flat Files / Objects Database (하드웨어)

`