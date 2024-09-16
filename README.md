DataBase
========
## RDBMS
Relational Database Management System의 약자 관계형 데이터베이스 관리 시스템 

ACID 규정 

&nbsp;&nbsp;원자성(Atomicity)

&nbsp;&nbsp;&nbsp;&nbsp;트랜잭션은 분해 불가한 최소의 단위

&nbsp;&nbsp;일관성(Consistency)

&nbsp;&nbsp;&nbsp;&nbsp;트랜잭션의 시작 전, 후로 일관성있는 데이터베이스 상태 유지

&nbsp;&nbsp;&nbsp;&nbsp;varchar(255)

&nbsp;&nbsp;독립성(Isolation)

&nbsp;&nbsp;&nbsp;&nbsp;하나의 트랜잭션 수행 중엔 다른 트랜잭션에 영향을 주어도, 간섭을 받아서도 안됨

&nbsp;&nbsp;지속성(Durability)

&nbsp;&nbsp;&nbsp;&nbsp;트랜잭션이 완료되고 정상처리가 되었다면 영구적으로 결과를 유지함 

OLTP ( Online Transaction Processing )

&nbsp;&nbsp;데이터 처리 ( insert , update , delete )
   
OLAP ( Online Analytical Processing )

&nbsp;&nbsp;데이터 분석, 집계 ( select )

NoSQL

&nbsp;&nbsp;Key-Value / Document / column family / graph 등 과 같은 schema free 인 모델을 지원........ 아 이건 나중에 하자


## Table

정규화

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





   
