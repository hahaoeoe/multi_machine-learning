**200213(목)**

1. RDBMS의 oracle을 활용하여 DB의 구조 익히기
2. Oracle 다운
3. sql plus 및 sql developer 다운 후 실행



**200214 (금)**

1. DB와 DBMS  개념
2. RDBMS 개념 
   * Relation, Relationship
   * tuple, field, key, shema
3. Sql developer를 활용하여 예제 연습 

> 그전에 먼저 ''작업관리자_서비스' 에서 oracle 파일 실행되고 있는지 확인
>
> 또는 명령 프롬포트(window) 에서 C:\user\student >netstat -ano
>
> 즉, Listener가 항시 구동되는 것이 중요하다. 구동 안되면 sql develpoer도 사용 불가능

 

* 예제) 대림_SELECT로 특정 데이터를 추출하기 <scott_oracle 에서 실행>
  1)  where 조건과 비교 연산자

  2) 논리 연산자

  3) between and 연산자

  4) in 연산자

  5) like 연산자와 와일드 카드

  6)  null을 위한 연산자

  7) 정렬을 위한 order by 절



* 예제) 한빛_02장 마당서점 DB 만들기 <madang_oracle 에서 실행>

  1) scott 계정에서 접속해제 후 새로 만들기

  > name은 system_oracle

  2) system_oracle에서 user madang 계정 생성 명령

  3) 새로운 madang_oracle 파일 만들어서  madang  DB 구축하기

  ==> table 만들고, 그 안에 내용 insert 하기





**200217 (월)**

*sql 기초*

1. 함수: select, from, where,  group by - having 

​      집계 함수: sum, avg, min, max

2. 조인
   * Inner join(내부조인; 일반적인 조인)
   * outer join(외부조인): left, right, full
3. 부속질의



**200218 (화)**

*sql 고급* 

1. 부속질의(subquery)
   * 스칼라 부속질의
   * 인라인 뷰
   * 중첩질의
2. 과제) 서브쿼리관련문제

