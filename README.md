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

NoSQL

&nbsp;&nbsp;Key-Value / Document / column family / graph 등 과 같은 schema free 인 모델을 지원........ 아 이건 나중에 하자




## OLTP ( Online Transaction Processing )
데이터 처리 ( insert , update , delete )
   
## OLAP ( Online Analytical Processing )
데이터 분석, 집계 ( select )

## Data File

&nbsp;&nbsp;MySQL

&nbsp;&nbsp;

&nbsp;&nbsp;MSSQL

&nbsp;&nbsp;

## Log

&nbsp;&nbsp;MySQL

&nbsp;&nbsp;MSSQL

## Backup

## Table

&nbsp;&nbsp;정규화

## Index

&nbsp;&nbsp;b-tree 

&nbsp;&nbsp;b+tree

&nbsp;&nbsp;clustered index

&nbsp;&nbsp;nonclustered index

&nbsp;&nbsp;index page 

## Query
&nbsp;&nbsp;실행순서
&nbsp;&nbsp;* SELECT
&nbsp;&nbsp;* FROM ( + Join ) 
&nbsp;&nbsp;* WHERE
* GROUP BY
* HAVING
* ORDER BY
> FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY

## Aurora RDS





   
