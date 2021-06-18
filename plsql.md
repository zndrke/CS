### PL/SQL

-  Procedural Language extention to SQL
- 오라클에서 지원하는 절차적 SQL
- 블록구조로 되어있고, PL/SQL 자신의 컴파일 엔진을 가짐



#### PL/SQL의 장점

- Block 구조로 다수의 SQL문을 한번에 ORACLE DB로 보내어 처리하기 때문에 수행속도를 향상시킬 수 있음
- Block 구조로 모듈화가 가능함
- 클 Block 안에 작은 Block을 위치할 수 있음
- 조건문(IF), 반복문(LOOP)을 사용하여 유연한 프로그래밍 가능
- VARIABLE, CONSTANT, CURSOR, EXCEPTION을 정의하고, SQL문장과 사용
  - VARIABLE : 변수
  - CONSTANT : 상수
  - CURSOR : 대용량 데이터를처리할 때, 데이터를 분할하여 처리 가능
  - EXCEPTION : 예외처리



#### 기본구조

- DECLARE, BEGIN, EXCEPTION, END가 한 블럭을 이룸
  - DECLARE : 변수를 정의하는 영역으로 생략 가능
  - BEGIN : 처리 로직 시작
  - EXCEPTION : 예외처리
  - END : 처리로직 종료
  - ;
- 블럭
  - 하나의 블럭 안에 여러 블럭 추가 가능
  - 블럭은 BEGIN으로 시작하고, END로 끝남

