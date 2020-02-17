# Python_machine 수업 흐름

**200203(월)**

1. 벡터라이징
2. coo, crs
3. TF-IDF
4. 교차 검증
5. Word2Vec, embeding



**200204(화)**

1.  [Word2Vec] Gensim을 활용한 Word2Vec으로 토지읽기
2. [텍스트분석] 베이즈정리로 텍스트분류하기
3.  퍼셉트론



**200205(수)**

1. [텍스트분석] 마르코프체인을 이용한 문장생성



**200206(목)**

1. 문장 생성

   * [챗봇구현] 챗봇만들기(마르코프체인기반) 

   

2. 반응형 웹

   * Webpage = html (구조, 내용) + CSS(레이아웃, 스타일) + JavaScript 
   * [jqeury] jquery-mobile
   * 과제: 쳇봇만들기(chatbot.py)의 html 꾸미기



**200207(금)**

1. 프론트엔드 (FrontEnd)
   * HTML
   * CSS
   * JavaScript
2. Webserver와 browser 등 정보 전달 과정
3. EditPlus를 통해 webpage 제작 및 구동





**200210(월)**

> 취업특강4 (김홍태 강사님)

1. 모의 면접(인성 +직무) - 면접 전략 + 면접 준비 + 실전 면접 훈련

* 면접의 이해 및 면접 전략
* 면접 시 어려움 및 성공 포인트

1. 토론 면접
   * 주제: 신종 코로나 바이러스 확산 방지를 위한 우한 뿐만 아니라 전체 중국인 방문 입국 금지 찬반

![59EDE8E1-614D-4598-8E86-C1E6E3541AAC](https://user-images.githubusercontent.com/58682936/74147716-24ae1980-4c47-11ea-9efd-3abb32de40dd.jpg)



**200211(화)**

1. Jquery를 활용한 웹 페이지 제작



**200212(수)**

1. xml
2. ajax
3. 과제): ajax 코드를 python 기반의 웹 서버에 구동되도록 구축 



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