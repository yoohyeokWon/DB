DataBase
=============

## RDBMS
******

Relational Database Management System의 약자 관계형 데이터베이스 관리 시스템 



1. ACID 규정 

&nbsp;&nbsp;원자성(Atomicity)
            
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;트랜잭션은 분해 불가한 최소의 단위

&nbsp;&nbsp;일관성(Consistency)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;트랜잭션의 시작 전, 후로 일관성있는 데이터베이스 상태 유지

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;varchar(255)

&nbsp;&nbsp;독립성(Isolation)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;하나의 트랜잭션 수행 중엔 다른 트랜잭션에 영향을 주어도, 간섭을 받아서도 안됨

&nbsp;&nbsp;지속성(Durability)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;트랜잭션이 완료되고 정상처리가 되었다면 영구적으로 결과를 유지함 



2. OLTP ( Online Transaction Processing )

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;데이터 처리 ( insert , update , delete )
   
3. OLAP ( Online Analytical Processing )

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;데이터 분석, 집계 ( select )

******

NoSQL

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Key-Value / Document / column family / graph 등 과 같은 schema free 인 모델을 지원 __아....... 이건 나중에 하자__


## Table

정규화

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정규화의 목표는 __테이블간 중복 데이터를 허용하지 않는다__임

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정규화의 장점으로는 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;데이터 변경 시 이상현상을 제거 할수있고,

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정규화된 데이터베이스 구조에서 새로운 데이터 타입의 추가로 인한 확장 시 구조를 변경하지 않거나 일부만 변경해도 되는거고

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;반대로 단점으로는

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;테이블 정규화로 인한 Join 연산이 많아지고 연산이 많아짐에 따라 응답속도가 느려질수 있다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이로 인해 __반정규화__라는 것도 적용할수있

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1정규화]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1정규화는 컬럼이 원자값(하나의 값)을 갖도록 테이블을 분리하는것이고, 아래 규칙을 만족해야함

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1. 각 컬럼이 하나의 속성만 가져아한다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2. 하나의 컬럼은 같은 종류의 데이터 타입을 가져야한다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3. 각 컬럼이 유일한 이름을 가져야한다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4. 컬럼의 순서가 상관 없어야한다 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;아래 예시 테이블은 제 1정규화 중 1번 규칙에 대한 조건이 성립하지 않는다 ( 2~4번 규칙은 성립 )

![image](https://github.com/user-attachments/assets/2298d19e-903f-4d7c-8ead-9fc1102c6593)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이제 1번 규칙까지 성립하게 변경하면 아래 형태로 테이블이 바뀌게 되고, 이러면 1정규화가 끝난다

![image](https://github.com/user-attachments/assets/23482dc4-1e0a-4d30-8681-d3cb243a27a7)



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2정규화]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3정규화]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[BCNF 정규화]



## Index

b-tree 

b+tree

clustered index

nonclustered index

index page 

## Query
실행순서
* SELECT
* FROM ( + Join ) 
* WHERE
* GROUP BY
* HAVING
* ORDER BY
> FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY


## MySQL
1. Architecture

2. Log

&nbsp;&nbsp;binlog

&nbsp;&nbsp;redo log 

3. Data file

&nbsp;&nbsp;디렉토리는 database name 으로 생성되고 tablename.frm 파일로 

https://fliedcat.tistory.com/80
https://blog.naver.com/bomyzzang/220135848812


## MSSQL

1. Architecture

2. Log

&nbsp;&nbsp;transaction log

&nbsp;&nbsp;

3. Data file

&nbsp;&nbsp;mdf

&nbsp;&nbsp;ldf

## Aurora RDS





   
