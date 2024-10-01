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

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정규화의 목표는 __테이블간 중복 데이터를 허용하지 않는다__ 임

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정규화의 장점으로는 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;데이터 변경 시 이상현상을 제거 할수있고,

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정규화된 데이터베이스 구조에서 새로운 데이터 타입의 추가로 인한 확장 시 구조를 변경하지 않거나 일부만 변경해도 되는거고

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;반대로 단점으로는

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;테이블 정규화로 인한 Join 연산이 많아지고 연산이 많아짐에 따라 응답속도가 느려질수 있다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이로 인해 __반정규화__ 라는 것도 적용할수있

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

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2정규화는 __완전 함수 종속__ 을 만족 해야한다는건데, 일단 규칙은 아래 2개이다 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1. 1정규화 규칙을 모두 만족

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2. 모든 컬럼이 부분 종속이 없어야 한다 ( 모든 컬럼이 완전 함수 종속을 만족해야 한다 )

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 그럼 이제 부분 종속이 무엇이냐 ?

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 기본키 중, 특정 컬럼에만 종속을 시켜야 한다 인데 글보단 눈으로 보는게 빠르니 

![image](https://github.com/user-attachments/assets/88ae33bf-9e80-4e8b-b2f3-cac1dca3bce7)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 위에 테이블 구조를 봤을때 기본키 _이름_ 과 _과목_ 에 대한 종속 컬럼은 _점수_ 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 기본키 _과목_ 에 대한 종속 컬럼은 _강의실_ , 이제 2정규화 조건을 맞춰 주기 위해 

![image](https://github.com/user-attachments/assets/a02d7f20-c7a3-45d3-9bf8-da97a66708dd)
![image](https://github.com/user-attachments/assets/23a7da86-0bf8-4738-afe2-20ad3576a2bb)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이렇게 2개의 테이블로 나누게 되면 2정규화 완성! 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3정규화]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3정규화는 _이행 종속_ 을 없애버리는 것 규칙은 아래 2개

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1. 2정규화 규칙을 모두 만족

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2. 기본키를 제외한 속성들 간 이행 종속이 없어야 한다

![image](https://github.com/user-attachments/assets/6d705de0-6d39-4208-aab7-87026c72c959)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이런 테이블이 있다고 해보자, 일단 이행 종속이란 A->B , B->C  일때 A->C 가 성립한다는 얘기인데 이게 딱 3정규화 규칙에 어긋난 상태

![image](https://github.com/user-attachments/assets/01d63505-b2c0-47ab-8782-159a5f2db6c8)
![image](https://github.com/user-attachments/assets/de52349d-75ae-4eb9-b047-6765d7c50247)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이렇게 바꿔주면 3정규화도 끝!

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[BCNF 정규화]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BCNF는 Boyce-Codd Normal Form 의 약자로 강화된 3정규화 라고 보면 된다 규칙은,

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1. 3정규화 규칙을 모두 만족

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2. 모든 결정자가 후보키 집합에 속해야됨

![image](https://github.com/user-attachments/assets/3fa0c42a-5635-432f-895d-68468561bec4)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이것도 그림으로 보면 기본키인 _학생명_ , _과목_ 으로 _교수명_ 을 알 수 있지만 같은 _과목_ 을 다른 교수가 가르칠 수 있어서

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; _과목_ -> _교수명_ 의 종속은 성립하지 않고 _교수명_ -> _과목_ 의 종속만 성립 할 수 있다 

![image](https://github.com/user-attachments/assets/917d8c86-46ac-466b-a2f0-2b1e37ab93a4)
![image](https://github.com/user-attachments/assets/81f6beb4-b08c-4df3-be7c-3592ee61e062)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 따라서 위에 처럼 테이블을 나누게 되면 BCNF 정규화 까지 만족 하게 된다.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; BCNF 정규화 다음으로 4정규화 ( 다치 종속 제거 ) , 5정규화 ( 모든 조인 종속 후보키를 통해서만 성립 )  까지있긴 하지만 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 5정규화 까지 모두 만족 하려면 실제 테이블에 컬럼이 딱 2개씩만 존재해야 하기때문에

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 실제 운영환경에서는 3정규화 이후의 정규화는 거의 사용하지 않으므로, 나중에 시간이 나면 그때 다시 정리

data type

문자형

1. CHAR

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;고정 길이 데이터 최대 255 Byte ( 지정 길이보다 짧을 경우 나머지 공간은 공백으로 채워짐 )

2. VARCHAR

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;가변 길이 데이터 최대 65535 Byte ( 지정 길이보다 짧을 경우 나머지 공간은 채우지 않음 )

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;varchar(255) 와 varchar(266) 의 차이

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;varchar 의 경우 저장할 값의 byte + 그 값의 길이를 나타내는 byte 를 저장하는데

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;255까지는 길이를 1byte 로 저장하지면 255를 초과하게 되면 길이를 1 byte로 저장할수 없기에 2 byte 로 저장

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;255를 초과하게 되면 2 byte씩 더 저장함..

3. TINYTEXT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;문자열 데이터 최대 255 Byte

4. TEXT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;문자열 데이터 최대 65535 Byte

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;text 와 varchar의 차이도 궁금 하겠지 ?

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;테이블을 생성 할 때 varchar(16382) 로 컬럼을 하나 생성 하고, 이후에 ADD COLUMN 으로 varchar(10)을 추가하면

![image](https://github.com/user-attachments/assets/ee92b5d4-0cd2-4245-a406-b6792afd25ff)


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이렇게 ERROR 1118이 발생 하는데, 테이블은 하나의 레코드가 저장할 최대 길이수인 65535 byte를 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;초과 했기때문에 새로운 컬럼을 추가하지 못하는것이고

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LOB (text , blob 같은 대용량 데이터를 저장하는 컬럼 )은 off-page라는 별도 외부 공간에 데이터를 저장 하지만

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MySQL server에서는 8100 byte 를 넘지 않으면 LOB을 inline 저장  , 8101 byte 부터는 off-page에 저장

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;( inline 저장이란 B-Tree 구조에 저장하는 것을 말한다 )

5. MEDIUMTEXT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;문자열 데이터 최대 16777215 Byte

6. LONGTEXT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;문자열 데이터 최대 4294967295 Byte

7. JSON

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JSON 문자열 데이터



숫자형

1. TINYINT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정수형 데이터  1 byte -128 ~ +127 or 0 ~ 255

2. SMALLINT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정수형 데이터  2 byte -32768 ~ +32767 or 0 ~ 65536

3. MEDIUMINT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정수형 데이터  3 byte -8388608 ~ +8388607 or 0 ~ 16777215

4. INT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정수형 데이터  4 byte -2147483648 ~ +2147483647 or 0 ~ 4294967295

5. BIGINT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;정수형 데이터  8 byte -9223372036854775808 ~ +9223372036854775807 

6. FLOAT

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;부동 소수형 데이터 4 byte

7. DECIMAL

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;고정 소수형 데이터 길이 + 1 byte

8. DOUBLE

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;부동 소수형 데이터 8 byte

날짜형

1. DATE

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 날짜(년도,월,일) 형태 3 byte 

2. TIME

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 시간(시,분,초) 형태 3 byte

3. DATETIME

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 날짜와 시간 형테 8 byte

4. TIMESTAMP

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 날짜와 시간 형테 4 byte

5. YEAR

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 년도 1 byte

이진 데이터

1. BINARY & BYETE

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; CHAR의 형태의 이진 데이터   255 byte

2. VARBINARY

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; VARCHAR의 형태의 이진 데이터   65535 byte

3. TINYBLOB

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이진 데이터 255 byte

4. BLOB

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이진 데이터 65535 byte

5. MEDIUMBLOB

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이진 데이터 1677215 byte

6. LONGBLOB

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 이진 데이터 4294967295 byte

Partition

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; partitioning 이란 테이블을 관리하기 쉬운 단위로 분리하는 것

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; MySQL에서 table partition 을 하게 되면 하나의 테이블로 보이지만 실제로는

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; partition key 별로 데이터 파일이 따로 생성 된다 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; partition 방법 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Vertical 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; column 단위로 데이터를 partition 하는 방법 , 데이터 정규화와 비슷하다

![image](https://github.com/user-attachments/assets/302dc5d5-795a-4983-b40b-7421dc455a7c)


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Horizontal 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; row 단위로 데이터를 partition 하는 방법 


![image](https://github.com/user-attachments/assets/7f4a2b01-c5a3-40e2-9b5c-608f58717b2f)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Horizontal partition의 종류

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1. RANGE

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 범위 단위로 데이터를 파티션하는 방법

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 주로 날짜, 시간을 파티션 키로 사용하는 경우 여기에 해당 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2. LIST

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 특정 값을 기준으로 데이터를 파티션하는 방법

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 주로 정형화 되어있는 카테고리 값을 파티션 키로 사용한느 경우 여기에 해당 ( ex : 성별 ) 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3. HASH

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 데이터를 적당히 나누기 힘들 경우 파티션 키를 해싱하여 모듈러 연산(%)을 통해 파티션하는 방법



## Index

인덱스 알고리즘

B-tree

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 최상위 하나의 루트 노드가 존재 하고 하위에 자식 노드가 붙어있는 형태

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 트리 구조의 최하위는 리프 노트 이고, 루트와 리프가 아닌 노드는 브랜치 노드라 한다. 구조는 아래
   
![image](https://github.com/user-attachments/assets/825edb10-1904-4c8a-8178-4c4fee18290e)



page 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 데이터 파일을 구성하는 기본적인 단위로 MySQL은 16KB MSSQL 8KB 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 데이터를 insert 하면 실질적으로는 page에 들어가게 되고 select를 하면 테이블을 읽는게 아닌 page에서 데이터를 읽어온다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 노드에서도 담을수 있는 인덱스의 사이즈도 16KB이며, 인덱스 컬럼을 잡을때 사이즈가 작을 수록 한 페이지에 많이담을수있음

clustered index

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 테이블 당 한개만 존재 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 클러스터 인덱스의 경우 저장 시 순서 보장을 위해 데이터를 물리적으로 재배열

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 테이블 자체가 인덱스이기 때문에 따로 인덱스 페이지를 생성하지 않고

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; non-clustered index 보다 조회 성능은 뛰어나지면 추가/수정/삭제 시 성능이 떨어질수 있음

nonclustered index

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 데이터 자채를 물리적으로 재배열하지 않고 인덱스 페이지만 정렬

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 인덱스 페이지를 따로 생성하기 때문에 추가적인 용량이 필요함

인덱스 선정 기준

1. 카디널리티 ( Cardinality ) 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 카디널리티란, value 에 대한 중복도이다 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 카디널리티가 높다 = 한 컬럼에서 갖고 있는 값의 중복도가 낮다 (대부분 다른 값을 가지고있는 경우다)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 카디널리티가 낮다 = 한 컬럼에서 갖고 있는 값의 중복도가 높다 (대부분 같은 값을 가지고있는 경우다)

2. 선택도 ( Selectivity )

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 선택도는 낮을수록 좋다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 선택도가 낮다 = 한 컬럼에서 갖고 있는 값 하나로 적은 개수의 row를 찾는다 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 선택도가 높다 = 한 컬럼에서 갖고 있는 값 하나로 많은 개수의 row를 찾는다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 선택도계산법 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 특정 값을 가진 컬럼의 row 수 / 총 테이블의 row 수 * 100

3. 조회 활용도

4. 수정 빈도

multi-column index 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 인덱스 생성 시 꼭 하나의 컬럼으로 인덱스를 생성하지 않고 여러개의 컬럼으로

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 인덱스를 생성할 수 있는데 이것을 멀티컬럼 인덱스라고 한다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 멀티컬럼 인덱스 생성 시 고민해야될 사항은 선행 컬럼을 어떤 것으로 선언 하냐이다

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WHERE 절에 필수로 들어가는 값을 선행 컬럼으로 선언하면 좋다 

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

![image](https://github.com/user-attachments/assets/da6c550a-b962-48bb-b03d-161207767c3c)

Mysql Server

스토리지 엔진

&nbsp;&nbsp; 실제 데이터를 저장하고 가져오는 역할 ( 핸들러를 의미함 )

핸들러 API

&nbsp;&nbsp; MySQL엔진과 스토리지 엔진이 데이터를 주고 받기 위한 API

MySQL 엔진

&nbsp;&nbsp; 1.쿼리 파서

&nbsp;&nbsp;&nbsp;&nbsp; 요청받은 쿼리를 MySQL이 인식할수 있게 트리형태의 구조를 만들어 내는 작업을 함

&nbsp;&nbsp;&nbsp;&nbsp; 문법오류 체크 쿼리파서가 진행

&nbsp;&nbsp; 2. 전처리기

&nbsp;&nbsp;&nbsp;&nbsp; 파서 과정에서 만들어진 파서 쿼리기반으로 구조적 문제적 확인 ( 테이블명, 컬럼명, 함수와 함수에전달할 객체 존재여부 접근 권한 등 )

&nbsp;&nbsp; 3. 옵티마이저

&nbsp;&nbsp;&nbsp;&nbsp; MySQL 은 CBO옵티마이저를 사용하기 때문에 쿼리를 가장 저렴한 비용으로 처리할지 결정 ( 두뇌 역할 )

&nbsp;&nbsp; 4. 실행엔진

&nbsp;&nbsp;&nbsp;&nbsp; 옵티마이저에 의해 생성된 실행계획대로 쿼리를 실행하는 역할이며 실제 실행엔진에서 스토리지 엔진과 지속적으로 핸들로 API를 통해 통신



![image](https://github.com/user-attachments/assets/44fe155b-142f-4cc3-80ae-56edf2ac094b)  

실제 쿼리가 실행되는 과정

5.7버전 까진 클라이언트단과 쿼리파서 사이에 __쿼리캐시__ 라는게 존재했지만 8.0 부터는 없어짐

쿼리캐시는 클라이언트의 요청을 쿼리파서에 넘기기전에 동일한 쿼리의 결과를 캐싱하고있는지 체크하는 역할이었음

삭제원인 - A 테이블의 데이터가 변경될 경우 쿼리캐시에 저장된 결과 중 A 테이블과 연관된 모든것들을 삭제해줘야 해서 동시 처리 성능 저하를 유발



MySQL 스레딩 구조

![image](https://github.com/user-attachments/assets/b9c12307-9de7-4229-bfa1-ae9582688737)

MySQL은 프로세스 기반이 아닌 스레드 기반으로 동작 ( 포그라운드 / 백그라운드 로 나뉨 )

포그라운드 스레드

&nbsp;&nbsp; 포그라운드 스레드는 MySQL 서버에 접속된 클라이언트 수만큼 존재

&nbsp;&nbsp; 사용자가 요청하는 쿼리문장을 처리하는 역할을 하며, 사용자의 작업을 마치고 커넥션이 종료되면 해당 스레드는 캐시로 돌아감

백그라운드 스레드

&nbsp;&nbsp; InnoDB 스토리지 엔진에서는 로그 스레드와 버퍼에 있는 데이터를 디스크로 내리는 쓰기 스레드가 가장 중요함

&nbsp;&nbsp; 쓰기 작업은 버퍼링해서 일괄 처리하는 기능을 갖고있음 

&nbsp;&nbsp; binlog 와 redo log 

&nbsp;&nbsp;binlog

&nbsp;&nbsp;&nbsp;&nbsp; binlog 는 DDL, DML을 통해 DB변경이 있을경우 mysql server에서 변경 이력을 기록하는 

&nbsp;&nbsp;&nbsp;&nbsp; 이진파일( select 문은 제외됨 ) 이며 SQL에 대응한 논리적인 로그라 한다 

&nbsp;&nbsp;&nbsp;&nbsp; 주로 사용되는 용도는 MySQL server 간 replication 또는 HA 구성에 사용된다 

&nbsp;&nbsp;&nbsp;&nbsp; 

&nbsp;&nbsp;redo log 

&nbsp;&nbsp;&nbsp;&nbsp; redo log 는 MySQL server 또는 OS 의 문제등으로 인하여 MySQL server 가 비정상적으로 종료됐을때 

&nbsp;&nbsp;&nbsp;&nbsp; 스토리지에 넘기지 못한 데이터를 잃지 않게 해주는 안전장치임. ( 안전장치 일뿐 유실이 없는건 아님 )

&nbsp;&nbsp;&nbsp;&nbsp; redo log 는 innodb 에만 있는 물리적 로그이며 ACID 를 보장하며, 엔진의 갱신정보를 일시적으로 보존한다      

&nbsp;&nbsp; 관련된 설정으로는 __innodb-flush-log-at-trx-commit__ 과 __sync-binlog__ 가 있다. 

&nbsp;&nbsp;&nbsp;&nbsp; trx commit 이 

&nbsp;&nbsp;&nbsp;&nbsp; 0 일땐, 클라에서 commit, rollback 시 메모리에 redo log 를 기록하고 1초에 한번씩 메모리에서 디스크로 redo log 를 내림

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 장점으론 디스크 I/O 가 줄어들지만, MySQL server 만 재부팅되어도 디스크에 내리지 않은 redo log 들은 증발

&nbsp;&nbsp;&nbsp;&nbsp; 1 일땐, 클라에서 트랜잭션이 실행 되면 메모리에 redo log 를 기록하고 commit 시 메모리에서 디스크로 redo log 를 내림

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 장점으론 데이터 유실이 없으나, 0번과 반대로 디스크 I/O 가 늘어남

&nbsp;&nbsp;&nbsp;&nbsp; 2 일땐, 클라에서 트랜잭션이 실행 되면 메모리에 redo log 를 기록하고 commit 시 O/S 버퍼로 redo log 를 내린 후 1초에 한번씩 디스크로 redo log 를 내림 

&nbsp;&nbsp;&nbsp;&nbsp; O/S 버퍼로 redo log 를 내린 후 1초에 한번씩 디스크로 redo log 를 내림 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 장점으론 OS 장애만 아니면 데이터 유실이 없으나 OS 장애 시 디스크로 내리지 않은 redo log 들은 증발

&nbsp;&nbsp;&nbsp;&nbsp; sync binlog 는 정수로 설정이 가능하며 매 N 개의 쿼리 이후 디스크와 동기화 한다는 설정이다

&nbsp;&nbsp;&nbsp;&nbsp; trx commit 과 동일하게 1이 가장 안정적이긴 하지만, sync binlog 가 1 이라 하더라도      

&nbsp;&nbsp;&nbsp;&nbsp; 시스템 장애가 발생하였을때 DB 데이터와 binlog 가 일치 하지 않을 가능성은 존재한다

&nbsp;&nbsp;&nbsp;&nbsp; innodb 테이블에 커밋이 실행 되면, MySQL 은 모든 트랜잭션 쿼리들을 bin log 에 기록하고 이후 innodb 트랜잭션을 커밋하는데

&nbsp;&nbsp;&nbsp;&nbsp; 저 사이에 장애가 발생하면 innodb 트랜잭션은 롤백, binlog 는 기록되어있을것이다.

&nbsp;&nbsp;&nbsp;&nbsp; 이러한 문제를 해결하기 위해 binlodg 와 innodb 테이블의 데이터 동기화를 보장는 

&nbsp;&nbsp;&nbsp;&nbsp; innodb-support-xa 변수 설정을 1 로 변경해줘야한다 .


## Aurora RDS

기본적으로 RDS Aurora MySQL 과 RDS MySQL 의 MySQL 엔진은 동일하나 가장 큰 차이점은 스토리지 이다 

Aurora 는 shared Storage 를 사용하고 replication도 binlog 기반이 아닌 Storage 기반으로 진행됨

Aurora MySQL을 띄우면 3개의 AZ에 각각 스토리지 노드가 생기고, 4개의 쓰기세트와 3개의 읽기 세트를 갖는 6개의 복사본 쿼럼을 사용

4개의 쓰기 세트란 스토리지(디스크)로 데이터가 입력될때 6개 노드 중 4개에 노드에 정상적으로 데이터가 들어가면 정상 

3개의 읽기 세트란 스토리지에서 데이터를 읽어올때 6개 노대 중 3개의 노드에서 동일한 데이터를 읽어오면 정상

![image](https://github.com/user-attachments/assets/13b21d10-2b5b-49e0-8310-34c591d1a1e0)

더 상세한 내용은 아래 aws 블로그를 참고하면 좋을듯

https://aws.amazon.com/ko/blogs/korea/amazon-aurora-under-the-hood-quorum-and-correlated-failure/








다음 시간은 replication ~ 
![image](https://github.com/user-attachments/assets/cfa5ec14-88f0-47dd-82df-b71ebcd532f6)


   
